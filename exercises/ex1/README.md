# Exercise 1 - See how it works (Simulator)

> **What you will learn:** how one plain-language question becomes a governed, verified answer. You will watch the agent scope to your authorizations, resolve the right views, generate and run a query, check its own work, and answer, then see it retry a hard question and refuse one that is out of a role's reach.

The Simulator is the one tab where you look under the hood. Everywhere else you see the answer; here you watch the agent work. One question becomes a sequence: scope to your authorizations, resolve the right views, generate a query, run it live, verify the result, answer. At query time the agent runs this as a bounded loop, and every step is capped by the user's authorizations.

You run a fixed set of verified questions as buttons here; there is no free text box on this tab. You will be able to write your own queries in the Freestyle tab after going through all the exercises.

> [!NOTE]
> The questions you can run depend on the role selected in **Logged in as** at the top. The tab shows only that role's questions, and a question runs as that role.

Open the **Simulator** tab.

## Step 1 - See the request you send

Click **Show request sent over A2A**. This is the exact A2A message the client sends the agent: the question, the target system, and your authorization grants. Same protocol you read about in Exercise 0, now carrying a real request.

## Step 2 - Run a clean, one-shot question

Leave **Logged in as** on the **Sales Representative** and run:

> `Show me all open sales orders`

Watch the Agent steps build in order: scope and resolve the CDS view candidates, generate SQL, execute against the live system, validate, compose the answer. This one lands first try. You never named a table or a view; the agent mapped "open sales orders" to the right view itself.

## Step 3 - Read the governance funnel

On that result, find the governance funnel: thousands of views in the system, narrowed to the views the role's grants reach, narrowed again to the few resolved for this question. The agent only ever considers data the signed-in role is allowed to reach.

> [!TIP]
> This funnel is the scope and resolve steps made visible. Scope caps the candidate set to the role's authorizations; resolve runs a scoped search over the semantic layer and reranks to the top few views.

## Step 4 - Look at the data it ran against

Expand the returned data. These are live rows, pulled from the SAP system when you ran the question. Read a few.

## Step 5 - Watch it retry

Still as the **Sales Representative**, run:

> `How many sales orders are blocked from delivery?`

This one is harder (it has to find the right status field). You will usually see it generate a query, hit a problem, reason, and generate a corrected query before it succeeds. That retry is the agent checking its own work before it answers.

> [!NOTE]
> This is the validate-and-retry loop. The agent only finalizes a query it has actually run and checked, so it catches and corrects a hallucinated column before it ever reaches you.

## Step 6 - Run the agent as the Finance Controller

The same agent serves any role; the questions just change with the job. Switch **Logged in as** to the **Finance Controller** and run:

> `List 10 profit centers for controlling area 0001 sorted by profit center id`

and

> `Show me the 5 most recent journal entries for company 0001 and list document types`

Neither is a sales question, and you still never named a table. Watch the funnel: it scopes to the finance role's own reach.

## Step 7 - Run the agent as the Purchaser

Switch **Logged in as** to the **Purchaser** and run:

> `Find the most expensive item in purchase order 5716435131`

Same agent again, a third domain. One agent, many jobs, each scoped to the role asking.

## Step 8 - Watch it refuse to guess

Set **Logged in as** to the **Utilities Billing Clerk**. This role has its own question button, the open-sales-orders question marked as outside its reach. Run it.

It is the same question you ran in Step 2; only the role changed. Sales data is outside the Utilities Billing Clerk's reach, so the agent concludes it cannot answer and says so. This is the governed behavior that makes it safe in front of real users: it stays inside the role's authorizations and tells you when it cannot help. Switch the role back when you are done.

## Step 9 - Run a complex cross-domain question

Finish on the **Full Access User**. This role has no authorization scope, so it reaches every view, which lets you ask something that spans more than one business object at once. Run:

> `First find the latest journal entry for company code 0001, then show its tax items`

This is two steps in one question: the agent first finds the latest journal entry, then follows it to its tax items and joins the two. Watch the Agent steps: it resolves more than one view, generates a query that links them, and composes a single answer. There is also a second complex question on this role if you want to push it further.

## Deep dive - read the generated SQL (optional)

Open the generated query on each result and read it. Two things the agent got right that a general model routinely gets wrong on SAP:

- **Predicate shaping.** In the blocked-from-delivery query, the filters are real technical codes: `"SDDocumentCategory" = 'C'`, `"OverallDeliveryBlockStatus" = 'C'`, and a block-reason check `"DeliveryBlockReason" <> ' '`. The agent knew the status fields and their code values, which is exactly what a plain language model guesses wrong.
- **Column discipline.** The open-sales-orders query selects a sensible set of columns and caps the rows (`LIMIT 30`). Output stays readable and the system stays protected.

These come from the SAP Domain Models grounding the agent. The agent embeds rules that cover the common pitfalls a general model hits when it writes SAP-specific query languages:

| Rule | What it handles | Example |
|---|---|---|
| **Value encoding** | Identifier fields padded to their stored key form | A human value like `100248` is matched to its padded key `0000100248` |
| **Date handling** | SAP's internal date and period formats | ABAP DATS format `YYYYMMDD` |
| **Parameterized views** | Views that need parameters get them in executable syntax | `FROM <SVC>.<VIEW> (P_DisplayCurrency => 'USD')` |
| **Predicate shaping** | Status and flag fields use the right technical codes | `WHERE "IsOpen" = 'X'`, not a guessed literal like `status = 'open'` |
| **Column discipline** | Output clamped to a sensible column set and row cap | Avoids queries that would overload the system |
| **Hallucination guard** | Selected fields verified against the current view metadata | Columns not found in the view metadata are intercepted before the query runs |

### Where the grounding comes from

The agent does not learn these rules at query time. An offline ingestion pipeline turns cryptic SAP metadata into a searchable semantic layer, and that layer (plus the rules above) is what the runtime loop draws on.

You will see more of these rules in action as you push the agent with your own questions in Freestyle.

Continue to - [Exercise 2 - Ask your data in plain language (Joule)](../ex2/README.md)
