# Exercise 1 - See how it works (Simulator)

The Simulator is the one tab where you look under the hood. Everywhere else you see the answer; here you watch the agent work. One question becomes a sequence: scope to your authorizations, resolve the right views, generate a query, run it live, verify the result, answer.

You run a fixed set of verified questions as buttons here. There is no free text box on this tab (that is Freestyle, at the end).

Open the **Simulator** tab.

## Step 1 - See the request you send

Click **Show request sent over A2A**. This is the exact A2A message the client sends the agent: the question, the target system, and your authorization grants. Same protocol you read about in Exercise 0, now carrying a real request.

## Step 2 - Run a clean, one-shot question

Run the first question (as the **Sales Representative**):

> `Show me all open sales orders`

Watch the Agent steps build in order: scope and resolve the CDS view candidates, generate SQL, execute against the live system, validate, compose the answer. This one lands first try. You never named a table or a view; the agent mapped "open sales orders" to the right view itself.

## Step 3 - Read the governance funnel

On that result, find the governance funnel: thousands of views in the system, narrowed to the views the role's grants reach, narrowed again to the few resolved for this question. The agent only ever considers data the signed-in role is allowed to reach.

## Step 4 - Look at the data it ran against

Expand the returned data. These are live rows from the SAP system, not a canned sample. Read a few.

## Step 5 - Watch it retry

Run the second question (still as the **Sales Representative**):

> `How many sales orders are blocked from delivery?`

This one is harder (it has to find the right status field). You will usually see it generate a query, hit a problem, reason, and generate a corrected query before it succeeds. That retry is the agent checking its own work, not returning the first thing it wrote.

## Step 6 - Watch it refuse to guess

Run the third question, as the **Utilities Billing Clerk**:

> `Show me all open sales orders`

Same question as Step 2, different role. Sales data is outside this role's reach, so the agent concludes it cannot answer instead of inventing a result. This is the governed behavior that makes it safe in front of real users: it stays inside the role's authorizations and tells you when it cannot help.

## Deep dive - what you just watched (optional)

The agent embeds rules for the SAP-specific pitfalls a general model trips on. In the traces you just ran, look for:

- **Value encoding**: a human value like 100248 is matched to its padded key 0000100248.
- **Date handling**: natural dates become SAP's internal date and period formats.
- **Parametrized views**: views that need parameters get them in the right executable syntax.
- **Predicate shaping**: status and flag fields use the correct technical codes, not a guessed literal.
- **Column discipline**: output is clamped to a sensible set of columns and rows.
- **Hallucination guard**: selected fields are checked against the current view metadata, so columns that do not exist are intercepted.

Continue to - [Exercise 2 - Ask your data in plain language (Joule)](../ex2/README.md)
