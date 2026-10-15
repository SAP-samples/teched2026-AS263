# Exercise 3 - Bring your own agent

The first two exercises reached the Domain Data Access Agent through surfaces we built: Joule and a custom app. This exercise flips it around. You build an agent of your own that calls the data agent over **A2A**, the Agent-to-Agent protocol. Your agent brings the logic. It borrows grounded, authorized SAP data by sending one A2A task.

This is the part you take home. You cannot take our hosted service with you, but you can take the shape: your agent asks the data agent for data, then reasons over and acts on what comes back.

Switch to the **Agents** tab. You build the agent as a short flow, top to bottom.

## The flow, in one minute

An agent flow here has four kinds of step:

- **Trigger** - what kicks the agent off. "A user asks" runs it live. "On a schedule" and "On an event" are the real production patterns, shown but not run here.
- **Query the Domain Data Access Agent** - the one step that leaves your agent. It sends an A2A task to the data agent and gets grounded rows back. This is the governed data-access call.
- **Reason** - your agent thinks about the rows: prioritise them, group them, assess the risk. Optional, and you can turn it off.
- **Act** - your agent does something with the result: summarise it for a manager, flag the urgent items, draft an email, make a to-do list, post a team update.

The Query step is the only one that touches SAP. Everything else works on the rows that step brought back.

## Exercise 3.1 - Build a flow: query, reason, act

The flow starts with a sensible default. Read it top to bottom first, then run it.

1. **Trigger.** Leave it on **A user asks** and pick a question from the dropdown.
2. **Query the Domain Data Access Agent.** This is the step that sends the A2A task. You do not configure it. It takes the trigger's question and asks the data agent.
3. **Reason.** Pick a goal, or type your own. Try **Assess the risk and name the top concerns**.
4. **Act.** Leave it on **Summarize for a manager**, or pick another.

Now click **Run agent** (top right) and watch each step light up in order:

- The **Query** step sends the A2A task to the data agent, which resolves the business entity, writes the query, runs it, and returns the rows. This takes a few seconds, because a real agent is doing real work on the other side.
- The **Reason** step takes those rows and applies your goal.
- The **Act** step turns the result into the output you chose.

Every step after Query works on the grounded rows the data agent returned. Your agent never saw the schema and never wrote a line of SQL.

## What the A2A call gives you, and what it does not

Look at the Query step's result. You get the **rows** and a **verification** flag. You do not get the SQL.

That is the point of the A2A boundary. Your agent receives the grounded, authorized result, not the query behind it. The data agent owns the SQL internally. Your agent never sees the schema, never writes SQL, and never holds a database credential. It sends a question and gets back data it is allowed to see.

## Exercise 3.2 - Design your own integration

You built one flow. Now think about wiring the Query step into an agent of your own. Walk through these, out loud with your partner or in your head:

1. **The call.** Your agent sends one A2A `message/send` task with the user's question. What does it do with the rows that come back: render them, feed them to a next step, summarize them? (That is exactly the Reason and Act steps you just built.)
2. **What A2A buys you.** List what your agent did not have to do: learn the data model, store credentials, write or validate SQL, keep up with schema changes. The data agent owns all of it behind the A2A boundary.
3. **Where it drops in.** The Query step is one tool call. It drops into a Joule skill, a LangChain or MCP tool, or any agent framework that can make an A2A request. The reasoning and the actions are yours. The grounded data is the agent's.

**Now you try.** Change the Reason goal or the Act, or add another Act step, and run it again. Same grounded data, a different thing done with it. That is your agent, built on a governed data primitive.

## Takeaway

You saw the Domain Data Access Agent three ways: inside Joule across two business systems, embedded in a custom app, and now as an A2A agent your own agent calls.

- **Understand:** one agent, across systems, with no schema knowledge from the user, and you proved it by opening the detail every time rather than taking our word for it.
- **The pattern:** a governed data agent you reach over A2A. Send a `message/send` task, get back grounded authorized data. Your agent brings the logic and the actions. The data agent brings the data.

That is the shape you design around in your own landscape, wherever your users and your agents already are.

That wraps up the hands-on exercises. Thanks for attending AS263. For questions and feedback, use the [Issues](../../issues) tab.
