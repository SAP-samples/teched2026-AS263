# Exercise 1 - See how it works (Simulator)

The Simulator is the one tab where you look under the hood. Everywhere else you see the answer; here you watch the agent work. One question becomes a sequence: scope to your authorizations, resolve the right views, generate a query, run it live, verify the result, answer.

You run a fixed set of verified questions as buttons here; there is no free text box on this tab. You will be able to write your own queries in the Freestyle tab after going through all the exercises.

One thing to know up front: the questions you can run depend on the role selected in **Logged in as** at the top. The tab shows only that role's questions, and a question runs as that role. Change the role and the question buttons change with it. That is the whole point: one agent, scoped per role.

Open the **Simulator** tab.

## Step 1 - See the request you send

Click **Show request sent over A2A**. This is the exact A2A message the client sends the agent: the question, the target system, and your authorization grants. Same protocol you read about in Exercise 0, now carrying a real request.

## Step 2 - Run a clean, one-shot question

Leave **Logged in as** on the **Sales Representative** and run:

> `Show me all open sales orders`

Watch the Agent steps build in order: scope and resolve the CDS view candidates, generate SQL, execute against the live system, validate, compose the answer. This one lands first try. You never named a table or a view; the agent mapped "open sales orders" to the right view itself.

## Step 3 - Read the governance funnel

On that result, find the governance funnel: thousands of views in the system, narrowed to the views the role's grants reach, narrowed again to the few resolved for this question. The agent only ever considers data the signed-in role is allowed to reach.

## Step 4 - Look at the data it ran against

Expand the returned data. These are live rows from the SAP system, not a canned sample. Read a few.

## Step 5 - Watch it retry

Still as the **Sales Representative**, run:

> `How many sales orders are blocked from delivery?`

This one is harder (it has to find the right status field). You will usually see it generate a query, hit a problem, reason, and generate a corrected query before it succeeds. That retry is the agent checking its own work, not returning the first thing it wrote.

## Step 6 - Run the agent as the Finance Controller

The same agent serves any role; the questions just change with the job. Switch **Logged in as** to the **Finance Controller** and run:

> `List 10 profit centers for controlling area 0001 sorted by profit center id`

and

> `Show me the 5 most recent journal entries for company 0001 and list document types`

Neither is a sales question, and you still never named a table. Watch the funnel: it scopes to the finance role's reach, not the sales role's.

## Step 7 - Run the agent as the Purchaser

Switch **Logged in as** to the **Purchaser** and run:

> `Find the most expensive item in purchase order 5716435131`

Same agent again, a third domain. One agent, many jobs, each scoped to the role asking.

## Step 8 - Watch it refuse to guess

Set **Logged in as** to the **Utilities Billing Clerk**. This role has its own question button, the open-sales-orders question marked as outside its reach. Run it.

It is the same question you ran in Step 2; only the role changed. Sales data is outside the Utilities Billing Clerk's reach, so the agent concludes it cannot answer instead of inventing a result. This is the governed behavior that makes it safe in front of real users: it stays inside the role's authorizations and tells you when it cannot help. Switch the role back when you are done.

## Step 9 - Run a complex cross-domain question

Finish on the **Full Access User**. This role has no authorization scope, so it reaches every view, which lets you ask something that spans more than one business object at once. Run:

> `First find the latest journal entry for company code 0001, then show its tax items`

This is two steps in one question: the agent first finds the latest journal entry, then follows it to its tax items and joins the two. Watch the Agent steps: it resolves more than one view, generates a query that links them, and composes a single answer. There is also a second complex question on this role if you want to push it further.

## Deep dive - read the generated SQL (optional)

Open the generated query on each result and read it. Two things the agent got right that a general model routinely gets wrong on SAP:

- **Predicate shaping.** In the blocked-from-delivery query, the filters are real technical codes, not guessed English: `"SDDocumentCategory" = 'C'`, `"OverallDeliveryBlockStatus" = 'C'`, and a block-reason check `"DeliveryBlockReason" <> ' '`. The agent knew the status fields and their code values, which is exactly what a plain language model guesses wrong.
- **Column discipline.** The open-sales-orders query selects a sensible set of columns and caps the rows (`LIMIT 30`) rather than pulling everything. Output stays readable and the system stays protected.

These come from the SAP Domain Models grounding the agent. Beyond what these two questions surface, the same rules also handle value encoding (matching a human value like 100248 to its padded key 0000100248), SAP date and period formats, parametrized views, and a guard that checks selected fields against the current view metadata so columns that do not exist are intercepted. You will see more of these as you push the agent with your own questions in Freestyle.

Continue to - [Exercise 2 - Ask your data in plain language (Joule)](../ex2/README.md)
