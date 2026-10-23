# AS263 - Powering autonomous agents with natural language data access

## Description

This repository contains material for the SAP TechEd 2026 session **AS263 - Powering autonomous agents with natural language data access**. 

Our workshop is a hands-on preview for the **SAP Domain Data Access Agent**, a governed natural-language-to-data access layer that will be released soon to Early Adopter Care (EAC) customers through the Joule Conversational Platform and also as a stand-alone agentic solution. Other business applications or agents speaking over Agent-to-Agent (A2A) protocol can leverage this agent to enable live, cross-domain data access to SAP S/4HANA and other SAP backend systems like SAP Ariba. As you will explore in this workshop, our agent streamlines data retrieval for business users and securely powers autonomous enterprise workflows.

\**The **SAP Domain Data Access Agent** is available as a multi-tenant, SAP-managed SaaS application in the Business Technology Platform (BTP)*

## Background

One key principal in the world of agentic AI is that agents are only as useful as the context that grounds them. We define agents as "autonomous software systems that use an artificial intelligence model to plan, reason, and take multi-step actions to achieve a specific goal." But reasoning over fixed, general knowledge only goes so far. Many enterprise agents fall short because they cannot reach the live enterprise data that most business-critical decisions depend on.

This gap applies to agents as well as the human decision-makers they support. Take an ordinary request an Internal Sales Representative gets when a customer calls about sales order 140780:

  1. When was the order created, and has it been delivered and invoiced yet?
  2. What is the total value of that customer's orders this year?

A business user often cannot answer these from a standard SAP Fiori tile, because the answer spans several linked business objects (the order, its delivery, its invoice, the customer) and you have to know where each field lives.
- If the data is not on a tile, the user raises a ticket for an internal support desk to triage.
- If it needs system knowledge, it goes to an SAP functional analyst, who locates the right tables, links them, and dumps the result to Excel.
- If the need is recurring, it escalates into a functional specification, and an ABAP developer builds a custom application that must be promoted through Dev, QA, and acceptance testing before it reaches production.

These processes take days or weeks, when in reality, modern business needs demand this gap to be closed in minutes.

Going through this session, you will see how the **SAP Domain Data Access Agent** solves these problems. You will see the same agent reason over live data under the hood, and then meet it again through several surfaces, used by many different business roles, to show its range and business value.

## Additional Technical Takeaways

In addition to understanding the business value and integration potential of our agent for you and your customers, you will gain a better understanding of how the agent:

- Propagates and scopes authorization based on the underlying user's role grants
- Resolves and shortlists data view or entity candidates for querying
- Handles lookups, filters, aggregations, and multi-view joins for complex questions

## The workshop app

The hosted workshop app presents the agent through a set of tabs. You work left to right:

1. **Start here**: tell us who you are (anonymous), and read up on the Domain Data Access Agent, the SAP Domain Models that power it, and the Agent-to-Agent (A2A) protocol.
2. **Simulator**: see how the agent works under the hood. Watch it scope to your authorizations, resolve the right data views, generate and run a query, verify the result, and answer. This is where you see the reasoning, including when it retries and when it decides it cannot answer.
3. **Joule**: the agent inside the conversational Joule assistant. You sign in through SAP Identity Authentication as a business role, then ask in plain language, used by many different business roles across more than one SAP system.
4. **Applications**: the same agent embedded inside custom dashboard applications, where each tile is a live agent call.
5. **Agents**: the agent as a tool your own agent calls over A2A, reasoning over and acting on the results.
6. **Freestyle**: unlocked once you finish the guided tabs. Ask anything you like, as any of a wide set of roles, and tell us how it did.

The Simulator is where you see how it works; Joule, Applications, and Agents are three ways the same agent is consumed. On the guided tabs you run a set of curated, verified questions; free-form questions are reserved for the Freestyle tab at the end.


## Requirements

The exercises run over the public internet against a hosted service. No VPN or special network access is required. On the hands-on laptop, you only need:

- A modern web browser (Chrome, Edge, or Safari)
- Workshop application link and access credentials which will be provided by the facilitators at the beginning of the session

## Workshop Facilitators

The facilitators for AS263 Hands-On Workshop are:

- **Evan Schweizer**
- **Raghunath Posa**
- **Kevin Terusaki**
- **Zhidong Ke**

Please raise your hand during the workshop and one of us will come over to support you and answer any questions! We will also share our email addresses during the session for follow ups and further inquiries!

## Exercises

Work through the tabs in order. Each tab tracks a few steps; finish all of them to earn the passcode that unlocks the Freestyle tab.

- [Exercise 0 - Start here](exercises/ex0/): tell us who you are, and read up on the Domain Data Access Agent, SAP Domain Models, and the A2A protocol.
- [Exercise 1 - See how it works (Simulator)](exercises/ex1/): watch the agent scope, resolve views, generate and run a query, verify, and answer, including a retry and a question it governs itself out of answering.
- [Exercise 2 - Ask your data in plain language (Joule)](exercises/ex2/): the agent inside the Joule assistant, across several business roles and a second SAP system (Ariba).
- [Exercise 3 - A custom app on the agent (Applications)](exercises/ex3/): pick a role, load a dashboard shaped for that job, and see the live agent call behind each tile.
- [Exercise 4 - Bring your own agent (Agents)](exercises/ex4/): build a flow where your agent calls the Domain Data Access Agent over A2A, then reasons over and acts on the result.
- [Exercise 5 - Freestyle](exercises/ex5/): enter the passcode, then ask your own questions as any of a wide set of roles, and leave feedback.

## Contributing
Please read the [CONTRIBUTING.md](./CONTRIBUTING.md) to understand the contribution guidelines.

## Code of Conduct
Please read the [SAP Open Source Code of Conduct](https://github.com/SAP-samples/.github/blob/main/CODE_OF_CONDUCT.md).

## How to obtain support

Support for the content in this repository is available during the actual time of the online session for which this content has been designed. Otherwise, you may request support via the [Issues](../../issues) tab.

## License
Copyright (2026) SAP SE or an SAP affiliate company and teched2026-AS263 contributors. Please see our [LICENSE](LICENSE) for copyright and license information. Detailed information including third-party components and their licensing/copyright information is available [via the REUSE tool](https://api.reuse.software/info/github.com/SAP-samples/teched2026-AS263).
