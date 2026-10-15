# Exercise 1 - Ask your data in plain language with Joule

This is the surface your users already know: Joule, the SAP assistant, as a plain chat box. You type a business question, and behind the chat the Domain Data Access Agent turns it into a live query against real S/4HANA data and hands back real rows. No SQL, no transaction code, no schema knowledge.

The questions below climb a ladder. Each step adds one thing the previous step did not do, and each step asks you to open the detail panel and read what the agent chose. Working the ladder is the point, so drive it yourself rather than reading past the answers. By the end you will have watched one agent handle lookups, filters, aggregations, and multi-view joins, all from plain English.

> **How to work each question:** ask it, read the answer, then open the SQL / detail panel and find the SAP view the agent selected. You never named it. That habit is what turns this from a demo you watch into something you can trust.

Exercises 1.1 and 1.2 run against the **SAP S/4HANA** tab. Exercise 1.3 switches to the **SAP Ariba** tab to show the same agent on a second business system. Both tabs are across the top of the Joule surface.

> **Set your role first.** On the **SAP S/4HANA** tab, open the "I am a" dropdown and pick **Internal Sales Representative**. The questions below are a sales rep's day, and the role tailors the data the agent reaches for. You can switch roles any time.

## Exercise 1.1 - Single-domain fluency

With the role set to **Internal Sales Representative**, start simple and add one twist at a time. Ask these in order:

1. > `Show me all open sales orders`
   A plain lookup. Open the panel and read the one view the agent selected. You never named it.
2. > `Show me the sales orders created in March 2026`
   Same domain, now with a date range. Notice the agent added a date filter you described in words, not in SQL.
3. > `Show me the invoicing status for sales order 140780`
   A status lookup on a single document. The agent resolves which view carries fulfillment status.

Now move from lists to numbers. The agent aggregates, it does not only fetch rows:

4. > `How many sales orders are blocked from delivery?`
   A count with a filter. The answer is a single number, not a list.
5. > `Show me a report of sales documents for customer USCU_ACNTR broken down by status`
   A grouped report. One question, a full breakdown by status.

**Now you try.** Write your own question that returns a *count* rather than a list. Hint: start it with "how many". Ask it, then open the panel and confirm the generated query aggregates instead of listing rows.

## Exercise 1.2 - Reasoning across views

A single hardcoded query reaches one table. The questions below need more than one business view joined together, and the agent works out the join on its own. This is the part a canned demo cannot fake.

1. > `Show me the document flow and status of sales order 140780 and all preceding documents`
   Open the panel. The agent joined more than one view to follow the document flow. List the views you see.
2. > `Show me the address of customer 1000654 and the total value of their sales orders since January 2026`
   This needs customer master data and sales order data together, joined and summed. You asked one plain-English question; the agent planned the join.

**Reflect.** In each of these, how many views did the agent touch, and did you name any of them? That is the difference between natural-language data access and a saved query behind a button.

## Exercise 1.3 - The same agent on a second system (Ariba)

Everything so far hit S/4HANA. The agent is not tied to one system. Switch to the **SAP Ariba** tab at the top of the Joule surface and ask about procurement data in the same plain English.

The Ariba tab has its own roles. Start as the **Sourcing Manager** (the default):

1. > `List all sourcing projects`
   A lookup against Ariba, not S/4HANA. Same chat, different business system.
2. > `Show me all active sourcing projects with their owners`
   A filtered list with an owner lookup.

Now switch the role to **Contract Manager** (the "I am a" dropdown) and ask:

3. > `Show me all contracts expiring in 2026`
   Contract data, a date filter, still plain English.
4. > `List all contract workspaces created in 2017`

Open the panel on any of these. The query is Ariba AQL, not SQL, because the agent is talking to a different system underneath. You did not change anything about how you asked. The agent worked out which system owns the data and how to query it.

> **The point of this exercise.** One agent, two systems, one way of asking. A business user does not need to know whether sourcing projects live in Ariba or sales orders live in S/4HANA. They ask, and the agent reaches the right system.

> If you want a self-paced recap of the S/4HANA story, use the **Guided walkthrough** button in the top bar. It replays the core sales prompts one at a time with narration.

## Summary

You drove one agent up a ladder of question shapes in S/4HANA (lookup, filter, status, count, grouped report, multi-view joins), then switched it to Ariba for sourcing and contracts without changing how you ask. Every time, you could open the panel and see which view or AQL the agent chose. Next you see the same agent embedded in a custom app.

Continue to - [Exercise 2 - A custom app on the agent](../ex2/README.md)
