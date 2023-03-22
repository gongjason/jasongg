---
title: Lessons from my startup's first off-site
description: In December, Firezone organized an off-site in California. Here's what we learned.
date: 2023-01-10
---

{{< notice note >}}
This post was written for and published on [Firezone's blog](https://www.firezone.dev/blog/first-offsite-retro/). We try to be transparent with everything, from the codebase to how we run our company.
{{< /notice >}}

My first tech job was at [Strong](https://www.strong.app/), a workout journal app that was pretty popular at the time. The founders were “digital nomads,” and the team was fully remote.

Back in 2016, this was highly uncommon.

We spent a lot of time creating processes to work together effectively on opposite sides of the world. One of these was meeting up in person regularly.

{{< figure src="https://user-images.githubusercontent.com/52545545/211626078-6f64a4f4-ec37-40cd-8bb5-a6b9b122f351.png" title="making remote work before it was cool">}}

At first, it was by accident. Since everyone was traveling anyway, we would coordinate being in the same city at the same time.

After working in person, we quickly noticed the way we worked remotely improved. People were more comfortable sharing their ideas, better at giving constructive criticism, and happier in general.

It just _felt_ better to work together in person.

## Why try this at Firezone?

If you believe Firezone can take a sizable bite out of the usual suspects of legacy remote access products, we’ll need to use every advantage.

As a startup, our biggest advantage is the ability to move quickly as a team.

This is much easier when everyone is comfortable sharing ideas and engaging in lively debate. Plus, it’s a lot more fun.

So we decided to try it out. After much planning, canceled bookings, and a few long flights, our team met in Santa Rosa, California.

{{< figure src="https://user-images.githubusercontent.com/52545545/216130487-bde66005-e3e0-4d88-a2d0-f9a842efc715.png" title="Our first office" >}}

## What did we do?

Our itinerary included architecture planning, a multi-day hackathon, and plenty of fun activities around the Bay Area.

{{< figure src="https://user-images.githubusercontent.com/52545545/211988059-02f3083a-116b-462e-a5ff-90af4fab63fc.png" >}}

The focus of the off-site was building. We each defined a few tasks that could realistically be completed by the end of the trip. So what did we work on?

- A new Firezone gateway (coming in 0.8!) that will eventually allow decoupling the web portal from the WireGuard data plane. A single Firezone web portal will soon be able to manage hundreds or even thousands of little Firezone gateways securing access to their respective private resources. More details to come!
- A [new REST API in 0.7](https://github.com/firezone/firezone/releases) to allow configuring Firezone in a more automatable way. Users love our snappy web portal, but nothing beats the power of an API for automation.
- Various documentation improvements to improve consistency between Omnibus and Docker sections, detail logging, and implement a v1 style guide.

Of course, no visit to the Bay Area would be complete without a tour of San Francisco. It rained most of the time, so we missed out on much of the picturesque hiking. But we still managed to snap some photos of the Golden Gate bridge and devour a few In-N-Out burgers.

Of special mention are the team dinners. Remote companies lack that familiar bond typically formed over team lunches in the office, so we sought to recreate that when we met in person. As an added bonus, we also split cooking duties. In many ways preparing food for your teammates is like opening a pull request: make something, request feedback on it, then merge and enjoy.

As someone whose culinary talents rival his passion for building security products, our resident chef [Jamil](https://twitter.com/jamilbk) led most of the culinary endeavors, including a 2-hour drive around Santa Rosa in search of live Dungeness crab.

{{< figure src="https://user-images.githubusercontent.com/167144/214394961-ecbff7d8-2f9c-48a6-a906-c387366169f3.jpeg" >}}

## Lessons learned for next time

Since this was our first off-site, some things could have gone better. Here’s a small list of hiccups and other things we’d do differently next time.

### Turn on low power mode

{{< figure src="https://user-images.githubusercontent.com/52545545/211503302-4b2e2e74-06e8-4929-aa5b-a336af25a450.png" >}}

If you’re booking an Airbnb, check for planned maintenance and outages! We were notified three days before arrival the power would be out during two full workdays.

Fortunately, we had a small power bank and mobile hotspot with unlimited data. Unfortunately, our lead Rust engineer’s beefy Linux machine only gets a single hour of battery life on a full charge.

When his machine died, we migrated to our local coffee shop, where power and WiFi were surprisingly abundant. _Editor’s note: Coffee shops in Santa Rosa are much more accommodating as a makeshift office than most in San Francisco._

When you’re building software, electricity and internet are vital -- splurge for that bigger battery bank and faster hotspot!

### Lumbar support is underrated

You’ll sacrifice some ergonomics when you work out of an Airbnb. Put a premium on large work surfaces, open common areas, and comfortable chairs. After a few days of working hunched over on a sofa, we learned the hard way.

Even better, leave heads down work until after the off-site. Instead, prioritize architecture discussions, brainstorming sessions, and design sprints.

### Stock the right fuel

We got carried away at Costco. Our out-of-town guests had never witnessed the spectacle of an American snack aisle. Fortunately, our talented engineers can turn Funyuns into elegant lines of Rust code (shoutout [@Gabi](https://github.com/conectado)).

All jokes aside, you’ll need the right fuel for your hackathons and deep product discussions. We recommend stocking up with plenty of coffee and healthy snacks.

### Plan ahead: it’ll pay off

As is often the case with startups, we planned the trip on short notice. This meant many last-minute restaurant bookings and trips to the store for basic supplies.

So, make a shopping list, book a few restaurants in advance, and have a backup plan. If you’re looking for a template, take a look at this [guide](https://posthog.com/handbook/company/offsites#how-to-plan-an-offsite-in-8-weeks---a-checklist) from our friends at PostHog. A great checklist is hard to beat.

## What’s next?

In a few short days, we:

- Aligned on Firezone’s product direction
- Made critical architecture decisions for the gateway and client apps
- Made significant progress on a few key features
- Bonded over great food, conversation, and Mario Kart

We could have accomplished some of these over a few long Zoom calls and chat threads, but not as quickly. There’s something about mind melding over a few days of intense work that’s hard to replicate.

So, will we have another off-site? Definitely!

Until next time!

:::info 👋 thanks for reading
Firezone secures remote access to private resources. This post doesn't have much to do about security, networking, or a fancy new feature. But hey, our product improves the remote work experience - organizing a great off-site helps too.

If you want to try it out, our [Docker install script](/docs/deploy) gets Firezone running in just a few minutes.
:::