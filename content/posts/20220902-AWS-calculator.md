---
title: "AWS VPN pricing is complicated"
date: 2022-09-02
---

As a recovering finance guy, I'm pretty happy when I can build something in a spreadsheet. It's nostalgic.

Since starting [Firezone](https://firezone.dev), I spend most days helping people with their VPN.

It wasn't long before someone complained about AWS' pricing.

It's unpredictable, and prone to getting out of hand.

![AWS](https://user-images.githubusercontent.com/52545545/205481407-a24b9e1f-e9f0-40bc-90e8-af6196a04537.png "Typical AWS horror story")

AWS VPN is no exception.

The post below was was originally shared on [r/sysadmin (on Reddit)](https://www.reddit.com/r/sysadmin/comments/x4312g/aws_vpns_pricing_is_hard_to_understand_so_i_built/). It's one of my most upvoted posts!

I attempt to explain how AWS VPN pricing works and what to watch out for.

## Original Post

Hey everyone!

Sometimes I work with IT teams to budget the price of different remote access products. AWS VPN is always challenging to forecast since there are so many cost variables. For example, we found the minimum cost for a single endpoint is $70 a month (assuming it's kept on 24/7), even if you don't connect to it at all. Most of the cost comes from target network associations.

To help with visualizing the cost, I built a  [cost calculator spreadsheet](https://docs.google.com/spreadsheets/d/1nSrriw0tSnb__VXf4w02GVWZC_yyoN9D2v8cDBwgioQ/edit?usp=sharing). I wanted to share it here in case it helps save a few dollars off your monthly bill. It's in Google Sheets, so please make a copy to use it yourself.

AWS has a pretty good cost calculator too, but having a few sample scenarios is the main section lacking from their docs.

### A few example scenarios

*The links go to nice charts in the spreadsheet.*

[**Scenario 1**](https://docs.google.com/spreadsheets/d/1nSrriw0tSnb__VXf4w02GVWZC_yyoN9D2v8cDBwgioQ/edit#gid=1947558723) **- Small team or personal project (1 VPC, 1 subnet, 3 users)**

Cost: $96 per month ($1,152 annually)

![scenario 1](https://user-images.githubusercontent.com/52545545/205481451-fab6cb6d-00a9-4e37-9005-5813bc1f1d17.png)

This is likely the most simple use case for AWS VPN. It highlights the high fixed cost of target network associations, which for smaller teams will make up the majority of your cost each month.

With such a small group of users, a bastion host or self-managing something like WireGuard can be a good low-cost option. In theory, if your VPN demands are infrequent, you can remove any target-network associations when you are not using the VPN.

[**Scenario 2**](https://docs.google.com/spreadsheets/d/1nSrriw0tSnb__VXf4w02GVWZC_yyoN9D2v8cDBwgioQ/edit#gid=596640168) **- Medium sized team (2 VPCs, 3 subnets, 10 users, split tunnel)**

Cost: $368 per month ($4,416 annually)

![scenario 2](https://user-images.githubusercontent.com/52545545/205481456-a8761f7d-f605-4a6b-92cf-89488f23eef6.png)

This is a more likely scenario for a team or small company. If you’re building software, your resources will be split across production, test, and dev environments. AWS themselves recommend[ splitting your environment across multiple accounts](https://aws.amazon.com/organizations/getting-started/best-practices) as your workloads become more complex.

Segregating your environments is great for your development processes and security, but it will increase your costs with AWS VPN. Each account requires a separate AWS Client VPN endpoint, and each subnet will require its own target network association. In this example, we use 4 to represent dev, test, and prod split across two availability zones.

[**Scenario 3**](https://docs.google.com/spreadsheets/d/1nSrriw0tSnb__VXf4w02GVWZC_yyoN9D2v8cDBwgioQ/edit#gid=768894664) **- Larger company (50 users, 1 on-prem environment, 4 subnets, full-tunnel)**

Cost: $850 per month ($10,200 annually)

![scenario 3](https://user-images.githubusercontent.com/52545545/205481458-adb792b9-9fa3-4d67-bd57-a4bb32c80851.png)

When the use case expands, so does the cost. Despite how much it costs, I think ultimately AWS VPN was built for this use case. It’s fully managed, highly available, and seamlessly ties into AWS IAM (federated to the IdP of your choice).

As the team gets larger, the client connection time will likely be the largest factor in cost. The data egress costs will also vary greatly depending on the company. In this example, we assumed 10 GB per user. That’s about 12 Zoom calls - maybe a bit conservative in today’s remote workplace.

### What goes into the cost?

*Costs are in $USD*

**Client VPN target network association ($0.10 to $0.15 per hour)**I asked my AWS rep if this can be disassociated when not used to save cost since it's the most significant contributor to fixed costs for smaller teams. I didn't get a straight answer, but let me know if you've tried this before.

**Client VPN connection time ($0.05 per hour)**Connection time is the aggregate time your VPN users have connected to the VPN (rounded up to the nearest hour).

**Site-to-site connection time ($0.05 per hour)**You are charged for each hour that your VPN connection is provisioned and available. A common use case is creating a connection between your data center or on-prem network with the AWS VPC.

**Egress traffic ($0.05 to $0.09 per GB)**Data egress is not usually a huge contributor to cost (for VPNs anyway) unless you turn on "full tunnel" traffic for clients. For the calculator, I ignored intra-region transfers. Those are priced at $0.01 per GB. Here's a [useful resource](https://aws.amazon.com/blogs/architecture/overview-of-data-transfer-costs-for-common-architectures/) from AWS on different types of data-transfer costs.

**Site-to-site global accelerator premiums ($0.05 per hour + $0.015 to $0.091 per GB)**Released in 2019, this feature improves VPN performance by routing VPN traffic through the AWS network instead of the public internet. This could be helpful when running latency-sensitive applications or workloads.

### Ways to reduce costs

*Let me know if you have other suggestions*

**Split Tunneling**When setting up your Client VPN Endpoint, the default config option is to use a full tunnel (split tunneling disabled). This means all traffic from your end users will be routed through the endpoint - even traffic destined for the public internet. Ingress is free, but with zoom calls (up to 3.8 Mbps up) being commonplace, the costs can rack up quickly.

**Terminate unused endpoints and associations**Target network associations are the main fixed cost of AWS VPN. If your usage is infrequent, you could disassociate the target networks until the route is needed again. Since AWS provides a [CLI command](https://docs.aws.amazon.com/cli/latest/reference/ec2/associate-client-vpn-target-network.html) and an [API endpoint](https://docs.aws.amazon.com/AWSEC2/latest/APIReference/API_AssociateClientVpnTargetNetwork.html) for configuring target networks, you could even set up a script to “shut down” the VPN when it is not needed.

**Set up a billing alarm**Most costs with AWS VPN are unavoidable, so set up an alert to know what you're spending. Using CloudWatch, you can create an alert that triggers when current spending passes above a set threshold. Take a look at the [AWS docs](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/monitor_estimated_charges_with_cloudwatch.html) on how to set this up.

\---

Thanks for reading! I know the [calculator](https://docs.google.com/spreadsheets/d/1nSrriw0tSnb__VXf4w02GVWZC_yyoN9D2v8cDBwgioQ/edit?usp=sharing) is not perfect, so please let me know how it can be improved, or give me a message if you'd like to work on the calculator directly.

I'm working on an open-source VPN called [Firezone](https://www.firezone.dev/). It's early in its development, but sometimes it could be a good alternative to AWS VPN. I hope it's alright to plug it here.
