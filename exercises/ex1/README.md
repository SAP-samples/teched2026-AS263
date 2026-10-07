# Exercise 1 - Natural-language data access with the Agent Simulator

The Agent Simulator is the guided surface for the data-access agent. This exercise proves the core idea of the session: one agent, many domains, no schema knowledge. It ends with a question that no single hardcoded query could answer.

Work through the questions in order. For each one, read the answer and then expand the agent's reasoning and SQL so you can see which business entities and SAP views it picked.

## Exercise 1.1 - Ask a question over the S/4HANA domain

The S/4HANA domain covers finance, controlling, procurement documents, and more.

1. In the Agent Simulator, select the S/4HANA domain. (If your build routes automatically, leave domain selection to the agent.)
   <!-- TODO(Evan): confirm whether the simulator exposes an explicit domain picker or auto-routes. -->
2. Ask:
   > `TODO(Evan): S/4HANA question #1 with confirmed backing data`
3. Expand the detail. Notice the views the agent chose. You did not name them.
4. Ask a follow-up that changes the shape of the answer, such as a filter or a grouping:
   > `TODO(Evan): S/4HANA question #2 (a variation of #1)`

<br>![S/4HANA question in the simulator](images/01_01_0010.png)

> **Point to make:** you wrote business language ("cost center", "overdue", "last quarter"), and the agent mapped it to CDS views and columns through the Domain Model.

## Exercise 1.2 - Same agent, a different domain (Ariba)

Now ask the same agent about procurement and spend in the Ariba domain. Nothing about the agent changed. Only your question did.

1. Ask:
   > `TODO(Evan): Ariba question with confirmed backing data, e.g. "Which suppliers have the longest payment terms?"`
2. Expand the detail and confirm the agent is resolving against Ariba entities now, not S/4HANA.

<br>![Ariba question in the simulator](images/01_02_0010.png)

> **Point to make:** this is where you show it is not hardcoded. The same agent handles a completely different domain because the Domain Model describes both. There is no per-question wiring.

## Exercise 1.3 - A cross-domain question

Finally, ask something that needs both domains at once. This is the part a single canned query cannot fake.

1. Ask:
   > `TODO(Evan): a genuine cross-domain question joining procurement (Ariba) and finance (S/4HANA). Confirm the deployed service actually answers it before relying on it live.`
2. Expand the detail. The agent should show that it pulled from both domains and joined the results.

> **Point to make:** this is the payoff. The agent broke a question down across domains and composed the answer. No human picked the views or wrote the join.

## Summary

You have driven one agent across the S/4HANA and Ariba domains and watched it answer a cross-domain question, all from plain English. Next you will see the same capability on a real customer problem.

Continue to - [Exercise 2 - An autonomous agent on a real problem (FDE scenario)](../ex2/README.md)
