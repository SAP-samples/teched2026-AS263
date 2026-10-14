# Exercise 1 - Ask your data in plain language with Joule

This is the surface your users already know: Joule, the SAP assistant, as a plain chat box. You type a business question, and behind the chat the Domain Data Access Agent turns it into a live query against real S/4HANA data and hands back real rows. No SQL, no transaction code, no schema knowledge.

The questions below climb a ladder. Each step adds one thing the previous step did not do, and each step asks you to open the detail panel and read what the agent chose. Working the ladder, not just reading the answers, is the point. By the end you will have watched one agent handle lookups, filters, aggregations, and multi-view joins, all from plain English.

> **How to work each question:** ask it, read the answer, then open the SQL / detail panel and find the SAP view the agent selected. You never named it. That habit is what turns this from a demo you watch into something you can trust.

All questions in this exercise run against the **S/4HANA** domain on the **SIX** landscape (the default). Leave the landscape toggle on SIX.

## Exercise 1.1 - Single-domain fluency

Start simple and add one twist at a time. Ask these in order:

1. > `Show me all open sales orders`
   A plain lookup. Open the panel: the agent picked `C_OpenSalesOrder`.
2. > `Show me the sales orders created in March 2026`
   Same domain, now with a date range. Notice the agent added a date filter you described in words, not in SQL.
3. > `Show me the invoicing status for sales order 140780`
   A status lookup on a single document. The agent resolves which view carries fulfillment status.

Now move from lists to numbers. The agent does not just fetch rows, it aggregates:

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

## Exercise 1.3 - Same intent, different words

The agent resolves what you *mean*, not the exact words you type. Prove it to yourself.

1. Pick any question from Exercise 1.1.
2. Ask the same thing two or three different ways. For example, for open sales orders you might try "which sales orders are still open?" or "list sales orders that haven't been completed".
3. Each time, open the panel and check the view it selected. You should land on the same view regardless of phrasing.

> If you want a self-paced recap of the whole Joule story, use the **Guided walkthrough** button in the top bar. It replays the core prompts one at a time with narration.

## Optional - Another domain (presenter-led)

The same agent is not limited to sales. The presenter may demonstrate a procurement question in the Ariba domain to show that nothing about the agent changes, only the question does. This is a demo rather than a hands-on step for now.

## Summary

You have driven one agent up a ladder of question shapes in S/4HANA: lookup, filter, status, count, grouped report, and multi-view joins, all from plain English, and every time you could open the panel and see which views it chose. Next you will watch the same agent carry a real customer problem end to end.

Continue to - [Exercise 2 - The same agent on a real customer problem](../ex2/README.md)
