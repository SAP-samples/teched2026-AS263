# Exercise 2 - Ask your data in plain language (Joule)

Joule is the surface your users already know: a plain chat box. You pick a role, pick a question, and behind the chat the Domain Data Access Agent runs a live query against real SAP data and hands back rows. No SQL, no transaction code, no schema knowledge.

You run verified questions as suggestion chips here; free-form questions are reserved for Freestyle. This exercise is about range: one agent, many roles, more than one SAP system.

Open the **Joule** tab.

## Step 1 - Connect the dots: see what is underneath

Click **Show system diagram** in the tab bar. It lays out the pieces:

> You -> SAP IAS (authenticate) -> Joule -> principal propagation -> Domain Data Access Agent -> SAP S/4HANA / Ariba

Joule is the chat surface; the Domain Data Access Agent is the engine underneath doing the resolve, generate, and execute work you watched in the Simulator. Your identity is propagated through, so every query runs with your own authorizations. Leave the diagram open; it animates as a question runs.

## Step 2 - Switch roles and watch the scope change

Open the **I am a** dropdown. There is a wide set of roles (Purchaser, Finance Controller, Internal Sales Representative, Maintenance Technician, Production Supervisor, and more). Pick a different role and the suggested questions change with it. Same agent, each role scoped to its own authorizations. This is the funnel from the Simulator, now from the user's seat.

## Step 3 - Ask a question

As the **Internal Sales Representative**, run the lookup:

> `when the sales order 140780 was created`

Then the cross-document question:

> `show me the delivery document details and the invoice details which are related to sales order 140780`

The second one needs more than one business view joined (the order, its delivery, its invoice). You asked once; the agent planned the join. This is the sales rep scenario from the workshop intro, answered in seconds.

## Step 4 - Read the generated query

On an answer, open **Show SQL** and read the query the agent generated and ran. You never wrote it and never named the views in it. Run the report-style question and read its query too:

> `check the following customer "Alpha Center (USCU_ACNTR)" and share a report showing a number of sales document by object status`

A count by status (a grouped report) from one plain-English request.

## Step 5 - Switch to a second system (Ariba)

Everything so far hit SAP S/4HANA. Switch to the **SAP Ariba** tab at the top, pick the **Sourcing Manager** role, and run:

> `List all sourcing projects`

Same chat, same way of asking, a different SAP system underneath. A business user does not need to know whether sourcing projects live in Ariba or sales orders live in S/4HANA. They ask, and the agent reaches the right system.

## Try more roles (optional)

Switch roles again and run that role's suggested questions. A Finance Controller pulling general ledger entries, a Purchaser on purchase orders, a Maintenance Technician on notifications: same agent, different role, different domain. That breadth is the point.

Continue to - [Exercise 3 - A custom app on the agent (Applications)](../ex3/README.md)
