# Setting up Discourse checklist


# Trust Levels

Discourse implements a system of [Trust Levels](https://blog.discourse.org/2018/06/understanding-discourse-trust-levels/). Although it has some sane defaults, it can be customized from the ground up.

- You can start with the defaults or some metrics that make sense for you and then adjust based on the community feedback. 
- Higher levels give "powers" to the community members that are akin to moderation. It is advised to keep a close eye on it and engage with your most active community members to assure the quality of experience in the community.

# Feature Requests

Discourse can also be used for feature requests, aleviating the need for yet another platform. To enable this functionality, we can simply create a category called "Feature Requests" and enable the [Voting plugin](https://meta.discourse.org/t/discourse-voting/40121?u=joebuhlig). 

Users can vote on their favorite features and chat bellow them, discussing amongst themselves and with the staff. Topics can be sorted by votes and moderators can manage the whole lifecycle of a feature request with either [closing, archiving or unlisting](https://meta.discourse.org/t/what-is-the-difference-between-closed-unlisted-and-archived-topics/51238) a topic.

Finally, there is the [Kanban theme component](https://meta.discourse.org/t/kanban-board-theme-component/118164) which can be used by the product team to easily visuzalise from inside the platform the state of each feature request (e.g ideation, implementation, etc.)

# Discourse - Slack

A lot of communities evolve in supporting both Slack and Discourse, usually starting with slack and then moving to a forum software.

## Integrations
Discourse has a first-class integration with Slack (amongst other chat platforms), which is highly customizable. It enables 2-way sync, meaning that Discourse posts/topics can be automagically be posted as a feed on slack while slack chats can be posted as transcripts on discourse. **All within the integration.**

➡️ Read more on [meta.discourse](https://meta.discourse.org/t/chatroom-integration-plugin-discourse-chat-integration/66522).

## Why a forum over a chatroom
- Questions/Answer are persisting and easily searchable, this leads to an organic Knowledge Base that is curated by the community itself.
- Slack requires more active participation to extract real value, otherwise it's a rolling feed of people who chat. It's hard to get a sense of what is going on if you don't visit often.


# General Tips

- If you want your company (teammates, colleagues, etc.) to be active on the Discourse, make sure they can see the activity that happens there without having to visit (which they won't until it becomes a habit). An easy way to do that is to pipe Discourse topics into a Slack channel that anyone in the company can join, and then see if anything comes up that they could provide a response to. To go a step further, create some fun incentives inside the company for interacting with the community on the Discourse, like a special sticker or t-shirt.

# Links

👋  Here's a post Josh Dzielak wrote about setting up Algolia's Discourse that goes over some key Discourse concepts: 

- [https://blog.algolia.com/algolia-community-forum-pioneer-badge/](https://blog.algolia.com/algolia-community-forum-pioneer-badge/)

This is an open source project Josh Dzielak to help handle webhooks from Discourse so it can be hooked up to other systems:

- [https://github.com/algolia/discourse-webhook-collector](https://github.com/algolia/discourse-webhook-collector)

# Contributors 
- [Josh Dzielak](https://github.com/dzello)
- [Odysseas Lamtzidis](https://github.com/odyslam)

# Resources

## Discourse Themes

 - [Developer’s guide to Discourse Themes](https://meta.discourse.org/t/beginners-guide-to-using-discourse-themes/91966)
 - [Beginners' guide to using Theme Creator and Theme CLI to start building a Discourse theme](https://meta.discourse.org/t/developer-s-guide-to-discourse-themes/93648)
 - [Designer's Guide to Discourse Themes](https://meta.discourse.org/t/beginners-guide-to-using-theme-creator-and-theme-cli-to-start-building-a-discourse-theme/108444)
 - [How do I install a Theme or Theme Component?](https://meta.discourse.org/t/how-do-i-install-a-theme-or-theme-component/63682)

