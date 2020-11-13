# Why, How, What

# Discourse forum checklist

- [ ] Decide on hosting method for Discourse
- [ ] Prepare branding assets (e.g logotype, icon, category images) according to the sizes mentioned in the same settings category
  - [ ] Make list assets and create them or make request from design team
- [ ] Prepare Code of Conduct, Terms of Service, Privacy Policy, and Forum Guidelines
- [ ] Assess & install social logins and decide on data strategy
- [ ] Align with team on top navigation bar information architecture
  - [ ] Install and setup required theme components
- [ ] Write announcement post that could be displayed as a banner post to all new users
- [ ] Write a small introductory post about the community team, who they are, their experience and what color they like. Make it personal.
- [ ] Setup categories, sub-categories, tags
- [ ] Assess on what custom user fields you want
- [ ] Evaluate sitemap/web-crawler settings
- [ ] Setup Private Groups
  - [ ] Setup "X employees" private group that people will automatically join based on the domain (@company) of the signup mail. 
  - [ ] Setup other public user groups that are relevant to the community (e.g MVP users)
  - [ ] Setup categories that are only accessible and/or visible to specific user groups
- [ ] Setup Google Analytics (add GA code from Google console)
- [ ] Setup Narrative Bot's message (welcome bot)
- [ ] Assess native discourse app banner notifications for mobile users
- [ ] Assess to enable/disable whispers and dms
- [ ] Setup default landing page
- [ ] Assess a Feature Requests category with the `voting` plugin enabled
- [ ] Assess a topic template (e.g Support category: template like in GitHub issues)
- [ ] Align with team on SQL queries which are relevant to your metrics/KPIs and you will use to monitor the community.
  - [ ] Assess automatic RESTful export of results to a data warehouse and/or visualization tool.
- [ ] Setup Discourse integrations
  - [ ] Setup Community CRM to integrate with Discourse
  - [ ] Setup integration for data extraction to company CRM
  - [ ] Setup SSO with main product (if SaaS)
  - [ ] Setup chat integration (e.g slack)
  - [ ] Setup integration with GitHub
  - [ ] Setup other integrations (e.g community plugins)
- [ ] Compile a support handbook for the rest of the team (engineers, product, etc.)


# Discourse Hosting

## Self-hosted Discourse

## Hosted Discourse 

# Trust Levels

Discourse implements a system of [Trust Levels](https://blog.discourse.org/2018/06/understanding-discourse-trust-levels/). Although it has some sane defaults, it can be customized from the ground up.

- You can start with the defaults or some metrics that make sense for you and then adjust based on the community feedback. 
- Higher levels give "powers" to the community members that are akin to moderation. It is advised to keep a close eye on it and engage with your most active community members to assure the quality of experience in the community.

# Feature Requests

Discourse can also be used for feature requests, aleviating the need for yet another platform. To enable this functionality, we can simply create a category called "Feature Requests" and enable the [Voting plugin](https://meta.discourse.org/t/discourse-voting/40121?u=joebuhlig). 

Users can vote on their favorite features and chat bellow them, discussing amongst themselves and with the staff. Topics can be sorted by votes and moderators can manage the whole lifecycle of a feature request with either [closing, archiving or unlisting](https://meta.discourse.org/t/what-is-the-difference-between-closed-unlisted-and-archived-topics/51238) a topic.

Finally, there is the [Kanban theme component](https://meta.discourse.org/t/kanban-board-theme-component/118164) which can be used by the product team to easily visuzalise from inside the platform the state of each feature request (e.g ideation, implementation, etc.)


# Integrations

## Slack

A lot of communities evolve in supporting both Slack and Discourse, usually starting with slack and then moving to a forum software.

Discourse has a first-class integration with Slack (amongst other chat platforms), which is highly customizable. It enables 2-way sync, meaning that Discourse posts/topics can be automagically be posted as a feed on slack while slack chats can be posted as transcripts on discourse. **All within the integration.**

➡️ Read more on [meta.discourse](https://meta.discourse.org/t/chatroom-integration-plugin-discourse-chat-integration/66522).

### Why a forum over a chatroom
- Questions/Answer are persisting and easily searchable, this leads to an organic Knowledge Base that is curated by the community itself.
- Slack requires more active participation to extract real value, otherwise it's a rolling feed of people who chat. It's hard to get a sense of what is going on if you don't visit often.

## Community CRMs

## Company CRMs (e.g Salesforce, Hubspot)

# General Tips

- If you want your company (teammates, colleagues, etc.) to be active on the Discourse, make sure they can see the activity that happens there without having to visit (which they won't until it becomes a habit). An easy way to do that is to pipe Discourse topics into a Slack channel that anyone in the company can join, and then see if anything comes up that they could provide a response to. To go a step further, create some fun incentives inside the company for interacting with the community on the Discourse, like a special sticker or t-shirt.


# Contributors 
- [Josh Dzielak](https://github.com/dzello)
- [Odysseas Lamtzidis](https://github.com/odyslam)


# Legal

## Code of Conduct

## Terms of Service

## Privacy Policy

## Forum Guidelines

Discourse has some defaults that are good enough for most cases. They are auto-populated when you create the forum.

✅ [Example](https://meta.discourse.org/faq)

# Resources

## Discourse Themes

 - [Developer’s guide to Discourse Themes](https://meta.discourse.org/t/beginners-guide-to-using-discourse-themes/91966)
 - [Beginners' guide to using Theme Creator and Theme CLI to start building a Discourse theme](https://meta.discourse.org/t/developer-s-guide-to-discourse-themes/93648)
 - [Designer's Guide to Discourse Themes](https://meta.discourse.org/t/beginners-guide-to-using-theme-creator-and-theme-cli-to-start-building-a-discourse-theme/108444)
 - [How do I install a Theme or Theme Component?](https://meta.discourse.org/t/how-do-i-install-a-theme-or-theme-component/63682)

## Links

👋  Here's a post Josh Dzielak wrote about setting up Algolia's Discourse that goes over some key Discourse concepts: 

- [https://blog.algolia.com/algolia-community-forum-pioneer-badge/](https://blog.algolia.com/algolia-community-forum-pioneer-badge/)

This is an open source project Josh Dzielak to help handle webhooks from Discourse so it can be hooked up to other systems:

- [https://github.com/algolia/discourse-webhook-collector](https://github.com/algolia/discourse-webhook-collector)
