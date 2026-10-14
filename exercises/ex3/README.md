# Exercise 3 - Bring your own agent

The first two exercises reached the Domain Data Access Agent through surfaces we built for you: Joule and the Utilities workspace. This exercise flips it around. Here the data access is a **tool** that any agent can call. Your agent brings the domain logic, and borrows grounded, authorized SAP data over a single call.

This is the part you take home. You cannot take our hosted service with you, but you can take the shape of the integration: what the tool looks like, what it returns, and where it drops into your own agent.

Switch to the **Agent** tab.

## Exercise 3.1 - Read the contract, then watch a real call

Before you type anything, read the **registered tool** card on the Agent surface. That card is the whole contract:

```
autosql.query(question: string) -> { sql: string, views: string[] }
```

In plain terms: your agent hands it a plain-English `question`, and it hands back a grounded `sql` query and the list of SAP `views` that query reaches. That is the entire surface area your agent has to understand.

Now watch it run. Reuse a question from Exercise 1 so you see the same capability arrive a different way:

1. Ask:
   > `Show me all open sales orders`
2. Watch the trace. You see the agent reason, then **call `autosql.query`** with your question, then receive a **tool result** containing the generated SQL and the views it selected.
3. Compare that SQL to what Joule showed you for the same question in Exercise 1. It is the same grounded query. One capability, reached first from a chat box and now from a tool call.

## What the tool returns, and what it does not

Read the trace carefully, because this is the real shape of a governed data-access tool.

- The tool returns a **grounded, schema-qualified query and the views behind it**. It resolved your plain-English question to the right SAP data, exactly as Joule did.
- The tool does **not** run that query here. It hands your agent an authorized query; your agent decides when, or whether, to execute it. In Exercise 1, Joule took that same grounded query and ran the execute step to show you rows. Here you are looking at the generate step on its own.

That separation is the point. The grounded query and the execution are two steps, and a calling agent controls the second one. That is what makes the data access governed: the agent never needs the schema, never holds database credentials, and never hand-writes SQL. It asks a question and gets back something safe to run.

## Exercise 3.2 - Design your own integration

You have seen the tool work. Now think about wiring it into your own agent. Walk through these, out loud with your partner or in your head:

1. **The call site.** Your agent has a user asking a business question. Instead of expecting the user to know the schema, your agent calls `autosql.query(question)` and gets back `{ sql, views }`. What does your agent do with each field?
2. **Where it drops in.** This same primitive can sit behind a Joule skill, or be registered as a tool in your own agent framework. The contract does not change. What changes is who calls it.
3. **What governed buys you.** List what your agent did *not* have to do: learn the data model, store credentials, write or validate SQL, or keep up with schema changes. The tool owns all of that.

**Now you try.** Ask one question of your own, within the domains and data you have seen in this session:

1. Type a plain-English question on the Agent surface.
2. Watch the agent call the tool, get a grounded query and views back, and compose its answer, with no schema input from you.
3. Confirm you could hand that same `{ sql, views }` result to any downstream step you control.

## Takeaway

You have seen the Domain Data Access Agent three ways: inside Joule, driving a real customer workflow, and as a tool your own agent can call.

- **Understand:** one agent, across domains, in multiple languages, with no schema knowledge from the user, and you proved it by opening the panel every time rather than taking our word for it.
- **The pattern:** a governed data-access tool, `autosql.query(question) -> { sql, views }`, that any agent can call in a single request to get a grounded, authorized query over live SAP data.

That is the shape you can design around in your own landscape, wherever your users and your agents already are.

That wraps up the hands-on exercises. Thanks for attending AS263. For questions and feedback, use the [Issues](../../issues) tab.
