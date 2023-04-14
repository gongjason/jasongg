Why invest in documentation?
I’ve written hundreds of help center articles. I don’t think I’ve put a fraction of the care I now put into documentation for Firezone. 

Why is that?

I notice this in most products that serve a user and a developer. Both articles are equally complex. 

User help is closer to an FAQ. There’s multiple forms of documentation, an FAQ is only a part of it.

:::note
I think help centers should be more like documentation. More context. People care about their products. Even non-technical users.
:::

Maybe it’s who the writer is. Or  how it’s written (zendesk vs. a static site generator).

Docs is product and UX

[graphic of things that don’t need a doc vs needs a doc]

User manuals are rare these days for both end users and admins. The products the require them are usually critical for business. The infrastructure your software runs on, the [], and your secure access platform.

When documentation needs to be consulted, it is as much part of the product as the UI, the features, and information architecture. After all, products are about solving problems and what good is a feature if you can’t figure out how to use it?

Docs is marketing

Much of marketing is about sending the right message to the right person at the right time. 

So, who is the right person? For us, it’s the admin or engineer that’s managing Firezone. The one dealing with early morning complaints of “my internet isn’t working” and the one on the hook when something goes wrong.

Our docs are the first place they look after landing on our homepage. And for most, they spend much more time in this first visit on our docs, than they do on our main website.

For this visitor, our message is that we understand the importance of documentation and that they’re experience using Firezo????

Self serve support

There are many ways to configure Firezone. We’ve deliberately built it to be extensible. Adding your own custom reverse-proxy, swapping out the Postgres database, and [] are just a few.

As a result, users often run into configurations our docs don’t cover, or edge cases we don’t support.

We found that being more detailed with our documentation results in less support requests. Inquiries almost immediately disappear for a topic once we create a doc for it.

We think it’s because there’s usually a significant amount of context to communicate in a support request. For most issues, it’s usually faster for users to look for the solution themselves and browse at their own pace.

This is obviously helpful for our team, as it frees time to focus on building the product.

Lessons learned writing docs

Prioritize the right docs with telemetry
To be honest, our docs vary in detail and polish. As a small team, the docs backlog competes with everything else we need to do (e.g., engineering, marketing, sales). So, understanding priority is important.

The most obvious way we do this is listening to our users. When we get the same support inquiries or see the same topics pop up in our Slack, we create a GitHub issue.

Though, this isn’t enough. We know for every GitHub issue or Discourse post, there’s 10x as many people who silently gave up. If you’re building a product, you use telemetry to tell you what features are valuable and the unexpected places where users get stuck. You can do the same for docs.

Website Analytics
A few metrics we pay attention to are:
* Time spent by page: Does the time spent on a page align with
* Bounce rate: which pages result in 
* Heatmaps
* User flows

Docs Search
Most static site generators for docs have a plugin, like Algolia. Once set up, you’ll see searches with no results, frequently asked questions, and even insights on context. 

Google Search Console
Unsurprisingly, just as many people search our docs with Google. This is usually the first step someone takes to arrive on our docs site. If you set up Google Search Console, you’ll see what searches your docs site ranks for.

Of particular value are searches where your docs rank poorly, when they shouldn’t. More on this below.

Streamline the process

As an open-source product, our GitHub repo is the center of our company and community. Since documentation changes often correspond to product changes, it made sense to put both under the same repo.

This allows us to create better processes to make sure docs are up to date. Our team is encouraged to keep code and documentation updates in the same PR. And certain docs, like the REST API, is generated automatically.

Since our main repo has the most visibility (ahem, stars), it also encourages more contributions from our community.

SEO, a necessary evil

Since Firezone is in active development, our deployment and configuration in	structions occasionally change.

![](https://user-images.githubusercontent.com/52545545/211517741-4efb596a-3765-40d8-b483-f807f3a88e86.png)

You’ll find third party guides of various quality in Google results. Recently, these started ranking higher than our docs. This is a problem because third party are quickly outdated and often inaccurate.

We didn’t think much of SEO when creating our docs, but we eventually found ourselves a part of the zero-sum game that appeases our Google overlords.

Wording matters
Try to match how your users word their searches. A small, but simple example is how adding the word “install” to our deployment documentation helped it rank higher than a few inaccurate third party guides. Though “deploy” is a more accurate term for our gateway, Google’s search telemetry showed almost everyone searches for “install”.

Give dedicated topics on their own page
Search engines have gotten better at ranking page sections in search results. But, overall we’ve found it helps rankings and also readability to split up topics into their own dedicated page.

Pick the right platform

We started our site on Jekyll and later migrated to docusaurus. Both were great, but small things like separating menu titles from page titles out of the box


Disclaimer: We have not consulted a SEO expert (yet).

Focus on what matters

The learnings here mostly deal with making the process of creating docs easier, and maximizing the value of docs you’ve already spent time creating.

At the end of the day, the quality of your writing and how it matches the intent of your audience trumps everything. We aren’t experts at that yet, but luckily, there’s plenty of amazing guides that cover this topic I’ve found helpful: 

Firezone’s docs need plenty of work. For starters we took []’s advice and revisited the intent of our docs. Beefing up the overview doc is a start.

If you found this post interesting, you can sign up for our newsletter to get notified of new posts.

That’s it for now!