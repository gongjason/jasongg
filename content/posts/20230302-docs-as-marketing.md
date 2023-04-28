---
title: Docs = product = marketing
description: Lessons learned writing documentation.
date: 2023-03-02
---

{{< notice note >}}
This post was originally written for [Firezone's blog](https://www.firezone.dev/blog/first-offsite-retro/). I never got a chance to publish it, but here it is!
{{< /notice >}}

I bet the last help center you visited was poorly written - lacking needed details, difficult to navigate, or just plain hard to understand.

For everyday products, I think good engineering and UX has taken its place. Software products rarely crash and buttons are where I expect them to be. Users also lose attention quickly. If I can't intuit my way around a product, it's going in the trash. That's what I assume as a PM.

So, there's few reasons to invest in the help center. They barely help with activation, retention, or other metrics companies measure. As a result, they often don't get much love.

{{< figure src="https://user-images.githubusercontent.com/52545545/232587175-a5eb192f-dbdc-489b-90a9-8d8b595edcb5.gif" title="">}}

Technical documentation is something else.

## Help center articles vs. docs. What's the difference?

I've written hundreds of help center articles. I can confidently say, I've put far less effort into writing them than I have into [Firezone's docs](https://www.firezone.dev/docs/).

The two are pretty different. In purpose, audience, and scope.

{{< figure src="https://user-images.githubusercontent.com/52545545/234777397-a02e110c-1862-4342-80cb-c2abce430dc2.png" title="Here's an example from Google Sheets on pivot tables. Left, help center, right, API docs.">}}

Help articles are for active users of a product. To troubleshoot issues, provide instructions on usage - like an FAQ. Users come with a specific question in mind, and value a quick in-and-out trip. Practically, help center articles don't need to be as detailed.

Technical documentation, on the other hand, is aimed at developers, system administrators, and other technical users who need to understand the underlying workings. Products that need docs are meant to be understood deeply, integrated, automated, and extended.

Sometimes docs also aim to educate the user on the underlying technology and design choices made in building the product. A personal favorite is [Fly.io](https://fly.io/docs/apps/volume-storage/).

The following are my learnings from a year of writing docs.

## Why invest in documentation?

### Docs is product and UX

{{< figure src="https://user-images.githubusercontent.com/52545545/235004563-836fe805-222d-4089-9912-79953e04d4e9.png" title="">}}

User manuals are exceedingly rare these days for products you use everyday. The products the require them are usually critical for business.

For us startup folk, it's the building blocks of your software product, the critical apps that run your business, and your BEKANT Ikea standing desk.

When documentation needs to be consulted, it is as much part of the product as the UI, the features, and information architecture. After all, products are about solving problems and what good is a feature if you can’t figure out how to use it?

### Docs is marketing

Marketing is about sending the right message to the right person at the right time.

So, who is the right person? Using Firezone as an example, it’s the admin or engineer that’s managing it. The one dealing with early morning complaints of “my internet isn’t working” and the one on the hook when something goes wrong.

Our docs are the first place they look after landing on our homepage. And for most, they spend much more time in this first visit on our docs, than they do on our main website.

With the docs, we want to showcase the functionality of our product concisely. We also want to show polish (as much as a small startup can), good UX, and build our credibility for the problem space.

### Self serve support

We’ve deliberately built Firezone to be extensible. Adding your own custom reverse-proxy, swapping out the Postgres database, and integrating a rare IdP are just a few ways to do it.

As a result, users often run into configurations our docs don’t cover, or edge cases we don’t support. This is pretty common for open-source projects.

We found that being more detailed with our documentation results in less support requests. Inquiries almost immediately disappear for a topic once we create a doc for it.

We think it’s because there’s usually a significant amount of context to communicate in a support request. For most issues, it’s usually faster for users to look for the solution themselves and browse at their own pace.

This is obviously helpful for our team, as it frees time to focus on building the product.

## Lessons learned

### Prioritize the right docs with telemetry

To be honest, our docs vary in detail and polish. With a small team, the docs backlog is always competing with everything else we need to do (e.g., engineering, marketing, sales). So, understanding priority is important.

The most obvious way we do this is listening to our users. When we get the same support inquiries or see the same topics pop up in our Slack, we create a GitHub issue.

Though, this isn’t enough. We know for every GitHub issue or Discourse post, there’s 10x as many people who silently gave up. If you’re building a product, you use telemetry to tell you what features are valuable and the unexpected places where users get stuck. You can do the same for docs.

Website telemetry is a good place to start. A few metrics we pay attention to are:

* Time spent by page: More time usually means more importance. Pay attention to outliers.
* Heatmaps: Find places on pages where users get stuck or spend more time.
* User flows: Improve navigation paths and structure.

Docs search is common with most static site generators, like Algolia. Once set up, you’ll see searches with no results, frequently asked questions, and even insights on what page searches occur.

Google search console is another resource. Unsurprisingly, just as many people search our docs with Google. This is usually the first step someone takes to arrive on our docs site. Of particular value are searches where your docs rank poorly, when they shouldn’t. More on this below.

### Streamline the writing process

As an open-source product, our [GitHub repo](https://github.com/firezone/firezone) is the center of our company and community. Since documentation changes often correspond to product changes, it made sense to put both under the same repo.

This allows us to create better processes to make sure docs are up to date. Our team is encouraged to keep code and documentation updates in the same PR. And certain docs, like the REST API, is generated automatically based on the code itself.

Since our main repo has the most visibility (ahem, stars), it also encourages more contributions from our community.

### Pick the right platform

We started our site on Jekyll and later migrated to [Docusaurus](https://docusaurus.io/). Small things like separating menu titles from page titles out of the box for SEO, and avaiability of plugins to make integrating docsearch simple makes it easier to focus on writing docs.

### SEO a necessary evil

Firezone is in active development, our deployment and configuration instructions occasionally change.

You’ll find third party guides of various quality in Google results. I imagine you'll find more as the product grows.

{{< figure src="https://user-images.githubusercontent.com/52545545/211517741-4efb596a-3765-40d8-b483-f807f3a88e86.png" title="">}}

Recently, these started ranking higher than our own docs. This is a problem because third party are quickly outdated and often inaccurate. We could also benefit from the page visitors.

We didn’t think much of SEO when creating our docs, but we eventually found ourselves a part of the zero-sum game that appeases our Google overlords.

So, take the time to invest in a bit of SEO. It doesn't take much, do a bit of keyword research, use keywords, link internally, and make pages snappy and mobile friendly.

The above problem was fixed by changing the word "deploy" to "install".

## Focus on what matters

At the end of the day, nothing trumps writing quality documentation. I'm not an experts at that yet, but luckily, you can always keep re-writing.

The learnings here mostly deal with making the process of writing easier, and maximizing the value of docs you’ve already spent time creating. Here's a few more of my favorite resources that go into more detail on the topic:

* On writing software documentation: [https://documentation.divio.com/](https://documentation.divio.com/)
* Examples of good docs: [Fly.io](https://fly.io/docs/), [Planetscale](https://planetscale.com/docs), [Stripe API](https://stripe.com/docs/api)

That’s it for now!
