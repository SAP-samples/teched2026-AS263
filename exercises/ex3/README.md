# Exercise 3 - Bring your own agent

The first two exercises reached the Domain Data Access Agent through surfaces we built for you: Joule and the Utilities workspace. This exercise flips it around. Here you watch a **second agent** reach the data agent the way your own agent would: over **A2A**, the Agent-to-Agent protocol. Your agent brings the domain logic and borrows grounded, authorized SAP data by sending one A2A task.

This is the part you take home. You cannot take our hosted service with you, but you can take the integration shape: how one agent discovers another, what it sends, and what comes back.

Switch to the **Agent** tab.

## What A2A is, in one minute

A2A is an open protocol for one agent to call another. The calling agent:

1. **Discovers** the target agent by reading its *agent card* at `/.well-known/agent.json`, which lists what the agent can do (its skills) and how to reach it.
2. **Sends a task** to the agent's endpoint using a `message/send` request: a message with the question and a little structured context.
3. **Receives a task result**: a status and, on success, one or more *artifacts* carrying the answer as structured data.

The data agent you have been using all session is a real A2A agent. Its card advertises one skill, `prepare-and-execute`: take a natural-language question, turn it into SQL, run it, and return the rows.

## Exercise 3.1 - Read the card, then watch the handoff

Before you type anything, read the **A2A skill** card on the Agent surface. It shows the contract your agent codes against:

```
message/send(question: string) -> Task { artifacts: [{ rows, verification }] }
```

Now run one. The suggestions are questions the data agent is ready to answer. Pick:

> `List the open clarification cases`

Watch the trace. It is the real A2A exchange, not a mock:

1. **Your agent reasons** that this needs live SAP data, so it delegates over A2A.
2. **It sends `a2a://autosql-agent/message/send`** with your question.
3. **The data agent runs its full loop** (resolve the business entity, write SQL, execute) and returns a **completed task** with the rows as a structured artifact.
4. **Your agent answers** from the grounded data it got back.

The call takes a few seconds, because a real agent is doing real work on the other side.

## What comes back, and what does not

Look at the result panel. You get the **rows** and a **verification** flag. You do **not** get the SQL.

That is the point of A2A here. Your agent receives the grounded, authorized result, not the query behind it. The data agent owns the SQL internally. Your agent never sees the schema, never writes SQL, and never holds a database credential. It sends a question and gets back data it is allowed to see.

## A2A is a conversation, not a single shot

Try a vaguer question, or one the agent cannot pin down from context:

> `Show me the cases`

Sometimes the data agent will come back `input-required`: instead of a result, it sends a **clarifying question** of its own. That is normal. A2A is multi-turn. A full calling agent would answer on the same conversation (the task's `contextId`) and the data agent would continue from where it left off. Watch for this, because it is how real agents negotiate rather than guess.

## Exercise 3.2 - Design your own integration

You have seen the handoff. Now think about wiring it into your own agent. Walk through these, out loud with your partner or in your head:

1. **Discovery.** Your agent fetches `/.well-known/agent.json`, reads the `prepare-and-execute` skill, and learns it can get SAP data by sending a task. What does your agent need to know beyond the card? (Not much. That is the point.)
2. **The call.** Your agent sends `message/send` with the user's question. What does it do with the artifact that comes back: render the rows, feed them to a next step, summarize them?
3. **What A2A buys you.** List what your agent did *not* have to do: learn the data model, store credentials, write or validate SQL, keep up with schema changes. The data agent owns all of it behind the A2A boundary.

**Now you try.** Ask one more of the suggested questions, or a close variation, and watch the full A2A round trip:

> `Why are utilities contracts blocked for billing?`

Confirm your agent sends the task, the data agent completes it, and the grounded rows come back, with no schema input from you.

## Takeaway

You have seen the Domain Data Access Agent three ways: inside Joule, driving a real customer workflow, and now as an A2A agent your own agent can call.

- **Understand:** one agent, across domains, in multiple languages, with no schema knowledge from the user, and you proved it by opening the detail every time rather than taking our word for it.
- **The pattern:** a governed data agent you reach over A2A. Discover its card, send a `message/send` task, get back grounded authorized data as an artifact. Your agent brings the logic; the data agent brings the data.

That is the shape you can design around in your own landscape, wherever your users and your agents already are.

That wraps up the hands-on exercises. Thanks for attending AS263. For questions and feedback, use the [Issues](../../issues) tab.
