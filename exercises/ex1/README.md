# Exercise 1 - Ask your data in plain language with Joule

This is the surface your users already know: Joule, the SAP assistant, as a plain chat box. You type a business question, and behind the chat the data-access agent turns it into a live query against real SAP data and hands back real rows. No SQL, no transaction code, no schema knowledge.

This exercise proves the core idea of the session: one agent, many domains, no schema knowledge. It ends with a question that no single hardcoded query could answer.

Work through the questions in order. For each one, read the answer and then expand the agent's reasoning and SQL so you can see which business entities and SAP views it picked. You never named them.

## Exercise 1.1 - Ask a question over the S/4HANA domain

The S/4HANA domain covers finance, controlling, procurement documents, and more.

1. In Joule, pick a suggested question or type your own.
2. Ask:
   > `TODO(Evan): S/4HANA question #1 with confirmed backing data`
3. Expand the detail. Notice the views the agent chose. You did not name them.
4. Ask a follow-up that changes the shape of the answer, such as a filter or a grouping:
   > `TODO(Evan): S/4HANA question #2 (a variation of #1)`

> **Point to make:** you wrote business language ("cost center", "overdue", "last quarter"), and the agent resolved it to the right CDS views and columns on its own.

## Exercise 1.2 - Same agent, a different domain (Ariba)

Now ask the same agent about procurement and spend in the Ariba domain. Nothing about the agent changed. Only your question did.

1. Ask:
   > `TODO(Evan): Ariba question with confirmed backing data, e.g. "Which suppliers have the longest payment terms?"`
2. Expand the detail and confirm the agent is resolving against Ariba entities now, not S/4HANA.

> **Point to make:** this is where you show it is not hardcoded. The same agent handles a completely different domain because the enriched metadata describes both. There is no per-question wiring.

## Exercise 1.3 - A cross-domain question

Finally, ask something that needs both domains at once. This is the part a single canned query cannot fake.

1. Ask:
   > `TODO(Evan): a genuine cross-domain question joining procurement (Ariba) and finance (S/4HANA). Confirm the deployed service actually answers it before relying on it live.`
2. Expand the detail. The agent should show that it pulled from both domains and joined the results.

> **Point to make:** this is the payoff. The agent broke a question down across domains and composed the answer. No human picked the views or wrote the join.

## Summary

You have driven one agent across the S/4HANA and Ariba domains from inside Joule, and watched it answer a cross-domain question, all from plain English. Next you will see the same agent carry a real customer problem end to end.

Continue to - [Exercise 2 - The same agent on a real customer problem](../ex2/README.md)
