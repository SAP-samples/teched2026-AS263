# Exercise 4 - Bring your own agent (Agents)

The first exercises reached the agent through surfaces we built: Joule and a custom app. This one flips it. You build an agent of your own that calls the Domain Data Access Agent over A2A. Your agent brings the logic; it borrows grounded, authorized SAP data by sending one A2A task.

This is the part you take home. You cannot take our hosted service, but you can take the shape: your agent asks the data agent for data, then reasons over and acts on what comes back.

Switch to the **Agents** tab. You build the agent as a short flow, top to bottom.

## The flow, in one minute

A flow has four kinds of step:

- **Trigger** - what starts the agent. "A user asks" runs it live. "On a schedule" and "On an event" are the real production patterns, shown but not run here.
- **Query the Domain Data Access Agent** - the one step that leaves your agent. It sends an A2A task to the data agent and gets grounded rows back. This is the governed data-access call.
- **Reason** - your agent thinks about the rows: prioritise, group, assess risk. Optional; you can turn it off.
- **Act** - your agent does something with the result: summarise for a manager, flag the urgent items, draft an email, make a to-do list, post a team update.

The Query step is the only one that touches SAP. Everything else works on the rows it brought back.

## Step 1 - Configure the flow

The flow opens on a sensible default. Working down the blocks, make three choices (each is a tracked step):

1. In the **Trigger**, pick a question from the dropdown.
2. In **Reason**, pick a goal (try **Assess the risk and name the top concerns**).
3. In **Act**, choose what the agent does with the result (for example **Summarize for a manager**).

The **Query** block in between needs no setup; it takes the trigger's question and sends the A2A task.

## Step 2 - Add a second action

Click **Add another action** below the Act step and pick a different action (for example **Draft an email** or **Make a to-do list**). Both actions will run on the same rows the Query step brought back, so your agent can do more than one thing with a single data call.

## Step 3 - Run it

Click **Run agent** (top right) and watch each step light up in order:

- The **Query** step sends the A2A task. The data agent resolves the business entity, writes the query, runs it, and returns the rows. This takes a few seconds, because a real agent is doing real work on the other side.
- The **Reason** step applies your goal to those rows.
- The **Act** step turns the result into the output you chose. If you added a second action, both run on the same rows.

Look at the Query step's result: you get the **rows** and a **verification** flag. That is the A2A boundary. Your agent receives grounded, authorized data; the query stays on the agent's side. It never sees the schema, never writes SQL, never holds a database credential. It sends a question and gets back data it is allowed to see.

## Where it drops in

The Query step is one tool call. It drops into a Joule skill, a LangChain or MCP tool, or any framework that can make an A2A request (one `message/send` task with the user's question). The reasoning and the actions are yours; the grounded data is the agent's. That is the shape you design around in your own landscape.

Continue to - [Exercise 5 - Freestyle](../ex5/README.md)
