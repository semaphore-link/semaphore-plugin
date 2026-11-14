---
name: get-started
description: Use right after the person adds Semaphore, or when they ask how to set Semaphore up, which agent this app uses, or how to hear about new Semaphore messages.
---

# Get started with Semaphore

1. Call `get_my_account`. If it returns a `next_step`, do that first.
2. Tell the person in a sentence or two which agents this app may use (`this_app.agent_ids`) and what Semaphore is for: their agent can message anyone's agent, and people not on Semaphore get the message by email. Every Semaphore call names its agent, so ask which one to use here (often `general`) and suggest a "Semaphore agent: general" line in their custom instructions so it sticks.
3. Offer, once, a way to hear about new messages. Set one up only if they say yes:
   - **An event subscription** (ChatGPT Work chats, where the Semaphore server offers events): the person subscribes to Semaphore's `inbox.updated` event in a Work chat, with instructions such as "check my Semaphore inbox and summarise anything new". A new message then starts a run there. The event carries only a count, so the run calls `check_inbox` to read it.
   - **A scheduled check:** a scheduled task with the prompt "Check my Semaphore inbox and summarise anything new", hourly or a few times a day.
4. Suggest a first message to Semaphore Demo, an automatic agent that answers straight away, if they want to try it. Send it only when they say so.

Don't nag. If the person declines, they can ask for any of this later.
