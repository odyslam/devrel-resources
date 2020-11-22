# Why, How, What

Because this is the document that I would have liked to find when researching to create our own Discourse forum at Netdata. A one-pit stop that aggregates bits of information and insights from blog posts, forum topics and professionals from the DevRel Collective community.

- [Why, How, What](#why-how-what)
- [Discourse forum checklist](#discourse-forum-checklist)
- [Discourse Hosting](#discourse-hosting)
  - [Self-hosted Discourse](#self-hosted-discourse)
    - [Quickstart container](#quickstart-container)
    - [Multi-container solution](#multi-container-solution)
    - [Kubernetes](#kubernetes)
  - [Hosted Discourse](#hosted-discourse)
- [Trust Levels](#trust-levels)
- [Feature Requests](#feature-requests)
- [Groups](#groups)
  - [Private Groups](#private-groups)
- [Integrations](#integrations)
  - [Export community data](#export-community-data)
  - [Social Logins](#social-logins)
    - [Some tips](#some-tips)
  - [Slack](#slack)
    - [Why a forum over a chatroom](#why-a-forum-over-a-chatroom)
  - [Community CRMs](#community-crms)
  - [Company CRMs (e.g Salesforce, Hubspot)](#company-crms-eg-salesforce-hubspot)
- [General Tips](#general-tips)
- [Legal](#legal)
  - [Code of Conduct](#code-of-conduct)
  - [Terms of Service](#terms-of-service)
  - [Privacy Policy](#privacy-policy)
  - [Forum Guidelines](#forum-guidelines)
- [Resources](#resources)
  - [Discourse Themes](#discourse-themes)
  - [Theme Components](#theme-components)
  - [Links](#links)
- [Contributors](#contributors)


# Discourse forum checklist

- [ ] Decide on [hosting method](#discourse-hosting) for Discourse.
- [ ] Decide the default landing page (latest topics, categories, etc.). **This must be set during the `/wizard` setup.**
- [ ] Prepare branding assets (e.g logotype, icon, category images) according to the sizes mentioned in the same settings category.
  - [ ] Make list of assets and create them or make request from design team.
- [ ] Prepare [Code of Conduct](#code-of-conduct), [Terms of Service](#terms-of-service), [Privacy Policy](#privacy-policy), and [Forum Guidelines](#forum-guidelines).
- [ ] Assess & install [social logins](#social-logins) and decide on data strategy.
- [ ] Align with team on top navigation bar information architecture.
  - [ ] Install and setup required [theme components](#theme-components).
- [ ] Write announcement post that could be displayed as a [banner post](https://meta.discourse.org/t/new-banner-topic-pin-type/16458) to all new users.
- [ ] Write a small introductory post about the community team, who they are, their experience and what color they like. Make it personal.
- [ ] Setup [categories](https://meta.discourse.org/t/how-to-add-categories/71859), [sub-categories](https://meta.discourse.org/t/understanding-subcategories/69564), [tags](https://meta.discourse.org/t/a-comprehensive-guide-to-discourse-tags/121041)
- [ ] Assess on what [custom user fields](https://meta.discourse.org/t/how-to-create-and-configure-custom-user-fields/113192) you want
- [ ] Evaluate [sitemap](https://meta.discourse.org/t/discourse-sitemap/40348)/web-crawler settings
- [ ] Setup [Groups](https://meta.discourse.org/t/guide-to-groups/110064)
  - [ ] Setup "X employees" [private group](#private-groups) that people will automatically join based on the domain (@company) of the signup mail. 
  - [ ] Setup other public user groups that are relevant to the community (e.g MVP users).
  - [ ] Setup categories that are only accessible and/or visible to specific user groups.
- [ ] Setup [Google Analytics](https://meta.discourse.org/t/how-to-put-traffic-analytics-code/88320) (add GA code from Google console)
- [ ] Setup [Narrative Bot's](https://meta.discourse.org/t/discourse-narrative-bot-beta-feedback/58621) message (welcome bot).
- [ ] Assess native [Discourse app banner notifications](https://meta.discourse.org/t/native-app-install-banner-for-android-and-ios/55056) for mobile users.
- [ ] Assess to [enable/disable whispers](https://meta.discourse.org/t/whispers-vs-staff-notes/95305) and dms
- [ ] Assess a Feature Requests category with the [voting plugin](https://meta.discourse.org/t/discourse-voting/40121?u=joebuhlig). enabled
- [ ] Assess a [topic template](https://meta.discourse.org/t/what-are-topic-templates/38295) (e.g Support category: template like in GitHub issues).
- [ ] Align with team on [SQL queries](https://meta.discourse.org/t/what-cool-data-explorer-queries-have-you-come-up-with/43516) which are relevant to your metrics/KPIs and you will use to monitor the community.
  - [ ] Assess automatic [RESTful export](https://meta.discourse.org/t/how-to-run-data-explorer-queries-with-the-discourse-api/120063/26) of results to a data warehouse and/or visualization tool.
- [ ] Setup Discourse integrations.
  - [ ] Setup [Community CRM](#community-crms) to integrate with Discourse.
  - [ ] Setup integration for [data extraction](#export-community-data) to company CRM.
  - [ ] Setup [SSO](https://meta.discourse.org/t/official-single-sign-on-for-discourse-sso/13045) with main product (if SaaS).
  - [ ] Setup [chat integration](#slack) (e.g slack)
  - [ ] Setup integration with [GitHub](https://meta.discourse.org/t/discourse-github/99895).
  - [ ] Setup other [integrations](#integrations) (e.g community plugins).
- [ ] Compile a support handbook for the rest of the team (engineers, product, etc.).
  - [ ] Gitlab, as always, can serve as an idea starting point with their open-sourced [handbook](https://about.gitlab.com/handbook/support/).


# Discourse Hosting

Discourse is an [open-source piece of software](https://github.com/discourse/discourse), thus the user can either select to self-host or use the hosted version of Discourse. 

## Self-hosted Discourse

Self-hosting has a number of advantages, the biggest of all is the ability to install any community and official plugin that exists, extending the forum (and the community) in any direction you seem fit. 

On top of that, you have direct access to the production database which you can easily have it cloned everyday and use the cloned database for analytics or enrichment of the company's data lake. The hosted Discourse can't provide direct access to the data-base, but you can use the [data explorer](https://meta.discourse.org/t/data-explorer-plugin/32566) plugin to run queries and extract the results [programmatically](https://meta.discourse.org/t/how-to-run-data-explorer-queries-with-the-discourse-api/120063) via a RESTful interface. 

### Quickstart container

Discourse has a guide on how to install the software in under 30 minutes, using a single docker container.

[Read the Guide](https://github.com/discourse/discourse/blob/master/docs/INSTALL-cloud.md)

### Multi-container solution

For the more advanced users, there is a guide on how to properly setup a multi-container setup, with the distinct pieces of Discourse in different containers (e.g postgreSQL).

This setup has a number of different improvements over the single-container setup, albeit more complex. 

I believe that for bigger setups where the community is much more mature and mission-critical, a multi-container (or even kubernetes) setup is warranted, so as to minimize downtime, enable easy maintenance and more.

[Read the Guide](https://github.com/discourse/discourse_docker)

### Kubernetes

Discourse is not officially supporting Kubernetes, but as with any hype, there are more than a handful of users who have attempted to make it play.

The results have been mixed and there is an ongoing discussion on [meta.discourse](https://meta.discourse.org/t/installing-on-kubernetes/49329).

Moreover, bitnami has released a [](https://hub.helm.sh/charts/bitnami/discourse)] for discourse. Note, that this release is not maintained by Discourse, thus you depend on bitnami to update the chart with the latest releases of Discourse.

## Hosted Discourse 

As the company underlines, since they give the entirety of their software stack for free, they are not a software company, but rather a hosting company. 

The [hosting plans](https://www.discourse.org/pricing) come in 3 tiers, with the gotcha being that you can't install any community plugin, but you have a predetermined list of supported plugins.

The important upside to hosted Discourse is that you can focus your energy on setting up the forum and the community strategy behind it, without having to deal with a self-hosted solution. On top of that, you have very good private support, which is another cost-saving feature.

All in all, **you buy time.**

Finally, it's very easy to transfer to a self-hosted version of Discourse once you feel comfortable and you have setup the infrastructure, and Discourse has a native export and import functionality.



# Trust Levels

Discourse implements a system of [Trust Levels](https://blog.discourse.org/2018/06/understanding-discourse-trust-levels/). Although it has some sane defaults, it can be customized from the ground up.

- You can start with the defaults or some metrics that make sense for you and then adjust based on the community feedback. 
- Higher levels give "powers" to the community members that are akin to moderation. It is advised to keep a close eye on it and engage with your most active community members to assure the quality of experience in the community.

# Feature Requests

Discourse can also be used for feature requests, aleviating the need for yet another platform. To enable this functionality, we can simply create a category called "Feature Requests" and enable the [Voting plugin](https://meta.discourse.org/t/discourse-voting/40121?u=joebuhlig). 

Users can vote on their favorite features and chat bellow them, discussing amongst themselves and with the staff. Topics can be sorted by votes and moderators can manage the whole lifecycle of a feature request with either [closing, archiving or unlisting](https://meta.discourse.org/t/what-is-the-difference-between-closed-unlisted-and-archived-topics/51238) a topic.

Finally, there is the [Kanban theme component](https://meta.discourse.org/t/kanban-board-theme-component/118164) which can be used by the product team to easily visuzalise from inside the platform the state of each feature request (e.g ideation, implementation, etc.)

# Groups

## Private Groups

Private groups are a great way for a team of users to communicate over issues that are either sensitive or highly specialized. For example, a private group and a private category for only this group regarding beta-testing the software and early feedback on features. 

In open-source projects, this could be used for a discussion board between the engineers of the company and the maintainers who maintain the binary packages of the product in various linux distributions. Depending on company policy, this group could have the discussions in a hidden category or a public category where only people from  certain groups can publish. This is important so as to keep the category on topic and without noise.

# Integrations

## Export community data

To export community data, there are 2 major mechanisms

- Discourse API: [Docs](https://docs.discourse.org/).
- Use the [Data Explorer plugin](https://meta.discourse.org/t/data-explorer-plugin/32566) to define arbitrary SQL queries and then call them via the [API](https://meta.discourse.org/t/how-to-run-data-explorer-queries-with-the-discourse-api/120063).
- If self-hosting, connect directly to the production PostgreSQL database or automatically mirror the database to an identical for analytics (e.g BigQuery).

Using these mechanisms, you can export any community data to the company's data warehouse (e.g BigQuery) and visualize them (e.g DataStudio). 

It is advised to perform such a scheme so that you can easily share community data with the rest of the team regarding the health of the community. Remember that the data only tell a part of the story, thus you will need to set the context and the narrative for the reports to truly reflect the community reality.

e.g A downward trend of support questions could signify that the product is improving.

## Social Logins

Discourse supports a large number of social logins, including custom Oauth providers (e.g SSO integration with the product).

Supported logins:

- [Facebook](https://meta.discourse.org/t/configuring-facebook-login-for-discourse/13394)
- [Google](https://meta.discourse.org/t/configuring-google-login-for-discourse/15858)
- [GitHub](https://meta.discourse.org/t/configuring-github-login-for-discourse/13745)
- [Custom Oauth](https://meta.discourse.org/t/login-to-discourse-with-custom-oauth2-provider/14717)
- [Twitter](https://meta.discourse.org/t/configuring-twitter-login-and-rich-embeds-for-discourse/13395)
- [LinkedIn](https://meta.discourse.org/t/linkedin-oauth2-plugin/46818)
  - Note that the Linkedin plugin does not offer a url to the user's linkedin profile. It is impossible to correlate forum user with linkedin user at this point. The plugin only provides you with the information that the user's email is being used behind a linkedin profile.
- [Office365](https://meta.discourse.org/t/microsoft-365-oauth2-plugin/51731)

Please note that depending on your hosting plan, some of the plugins may not be available.


### Some tips

Take note that depending on which type of login the user uses, he/she will reveal a part of their total digital identity to you. This is an important decision that should not be made lightly, because offering a limited number of options, nudges your users towards these options.

If they sign in using GitHub, you will be able to correlate their forum activity with their GitHub contributions , to your projects and others. If they use twitter, you will be able to see their reach. Having tens of thousands of followers means that the user is an influencer in their respective field, so you may want to take notice.

On the other hand, if your product supports SSO, this creates powerful synergy, as you will know the product use of most community users, increasing your capacity for effective support and understanding if the feedback you receive comes from a seasoned user or not.

Finally, it is advised to have a discussion with various stakeholders in your company (e.g sales, marketing, product) and see what identities would be interesting to them. What identities do **they** want to see enriched with data regarding the community activity?

So, it is best to firstly align internally for a data strategy, see what information is more useful to you and then decide on what logins you want to offer. Note that the more options you offer, the more widespread the users will be, thus if you offer low value logins, a percentage of users will use that login instead of the high value alternative.

## Slack

A lot of communities evolve in supporting both Slack and Discourse, usually starting with slack and then moving to a forum software.

Discourse has a first-class integration with Slack (amongst other chat platforms), which is highly customizable. It enables 2-way sync, meaning that Discourse posts/topics can be automagically be posted as a feed on slack while slack chats can be posted as transcripts on discourse. **All within the integration.**

➡️ Read more on [meta.discourse](https://meta.discourse.org/t/chatroom-integration-plugin-discourse-chat-integration/66522).

### Why a forum over a chatroom
- Questions/Answer are persisting and easily searchable, this leads to an organic Knowledge Base that is curated by the community itself.
- Slack requires more active participation to extract real value, otherwise it's a rolling feed of people who chat. It's hard to get a sense of what is going on if you don't visit often.

## Community CRMs

Community CRMs are platforms that enable you to analyze your community on the platforms that exist, creating a central source of truth of the community members regarding their identity and community touchpoints. The useful part comes when the platform is able to merge different digital identities that belong to the same person (e.g Discourse and GitHub account), thus giving you a view of the user's journey in your community as a whole.

These tools  can directly hook up on your discourse instance and gather whatever information they deem important. The abstraction is an important one, since it saves considerable time from the part of the Developer Relations team.

Using these tools you can:

1) Analyze the health of the community as a whole
2) Analyze the health of the community on each respective platform
3) See the user's journey inside the community, empower you to interact with the users on important milestones:
   1) First topic on the forum
   2) First contribution on GitHub
   3) First interaction in the community as a whole (across all platforms)
4) See information about the user that is publicly available
   1) e.g company or email through GitHub profile

All the following options work with Discourse:

1) [SavannahHQ](https://savannahhq.com/)
2) [Orbit.love](https://orbit.love/)
3) [GrimoireLab](https://chaoss.github.io/grimoirelab/)

## Company CRMs (e.g Salesforce, Hubspot)

# General Tips

- If you want your company (teammates, colleagues, etc.) to be active on the Discourse, make sure they can see the activity that happens there without having to visit (which they won't until it becomes a habit). An easy way to do that is to pipe Discourse topics into a Slack channel that anyone in the company can join, and then see if anything comes up that they could provide a response to. To go a step further, create some fun incentives inside the company for interacting with the community on the Discourse, like a special sticker or t-shirt.

# Legal

## Code of Conduct

The code of conduct is a very important tool, especially for bigger communities where they attract a large number of people. It is no secret in the internet, that communities can turn toxic quite fast, with people creating a negative impact on the community and it's growth potential. In that regard, the code of conduct is a clear set of laws that the community abides by. In case of violation, you have clear grounds to apply any measure you deem necessary.

**Some examples:**

- [Mautic](https://www.mautic.org/code-of-conduct)
- [Netdata](https://learn.netdata.cloud/contribute/code-of-conduct)
- [SuiteCRM](https://docs.suitecrm.com/community/code-of-conduct/)
- [Mozilla](https://www.mozilla.org/en-US/about/governance/policies/participation/)

**Additional Resources:**

- [CoC Assessment Tool](https://mozilla.github.io/diversity-coc-review.io/)
- [We don't do that here, by Aja Hammerly](https://thagomizer.com/blog/2017/09/29/we-don-t-do-that-here.html)

## Terms of Service

It offers legal protection for your company.

## Privacy Policy

If clearly states when and how you can communicate with forum users and most importantly how you handle their personal data.

## Forum Guidelines

Discourse has some defaults that are good enough for most cases. They are auto-populated when you create the forum.

✅ [Example](https://meta.discourse.org/faq)

# Resources

## Discourse Themes

 - [Developer’s guide to Discourse Themes](https://meta.discourse.org/t/beginners-guide-to-using-discourse-themes/91966)
 - [Beginners' guide to using Theme Creator and Theme CLI to start building a Discourse theme](https://meta.discourse.org/t/developer-s-guide-to-discourse-themes/93648)
 - [Designer's Guide to Discourse Themes](https://meta.discourse.org/t/beginners-guide-to-using-theme-creator-and-theme-cli-to-start-building-a-discourse-theme/108444)
 - [How do I install a Theme or Theme Component?](https://meta.discourse.org/t/how-do-i-install-a-theme-or-theme-component/63682)

## Theme Components

## Links

👋  Here's a post Josh Dzielak wrote about setting up Algolia's Discourse that goes over some key Discourse concepts: 

- [https://blog.algolia.com/algolia-community-forum-pioneer-badge/](https://blog.algolia.com/algolia-community-forum-pioneer-badge/)

This is an open source project Josh Dzielak to help handle webhooks from Discourse so it can be hooked up to other systems:

- [https://github.com/algolia/discourse-webhook-collector](https://github.com/algolia/discourse-webhook-collector)

# Contributors 
- [Josh Dzielak](https://github.com/dzello)
- [Odysseas Lamtzidis](https://github.com/odyslam)