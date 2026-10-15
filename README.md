# AS263 - Powering autonomous agents with natural language data access

## Description

This repository contains material for the SAP TechEd 2026 session **AS263 - Powering autonomous agents with natural language data access**. 

Our workshop is a hands-on preview for the **SAP Domain Data Access Agent**, a governed natural-language-to-data access layer that will be released soon to Early Adopter Care (EAC) customers through the Joule Conversational Platform and also as a stand-alone agentic solution. Other business applications or agents speaking over Agent-to-Agent (A2A) protocol can leverage this agent to enable live, cross-domain data access to SAP S/4HANA and other SAP backend systems like SAP Ariba. As you will explore in this workshop, our agent streamlines data retrieval for business users and securely powers autonomous enterprise workflows.

\**The **SAP Domain Data Access Agent** is available as a multi-tenant, SAP-managed SaaS application in the Business Technology Platform (BTP)*

## Background

One key principal in the world of agentic AI is that agents are only as useful as the context that grounds them. We define agents as "autonomous software systems that use an artificial intelligence model to plan, reason, and take multi-step actions to achieve a specific goal." But reasoning over fixed, general knowledge only goes so far. Many enterprise agents fall short because they cannot reach the live enterprise data that most business-critical decisions depend on.

This gap applies to agents as well as human business users and/or decision-makers. Take these two ordinary business questions from the perspective of an Internal Sales Representative:

  1. Which sales orders are blocked from delivery?
  2. Why are these contracts blocked for billing?

A business user may not be able to answer these from a standard SAP Fiori tile. If not, the user must create a ticket for triaging by an internal support desk: 
- If it needs system knowledge, it goes to an SAP functional analyst, who locates the right tables, links them, and dumps the result to Excel 
- If the need is recurring, it escalates into a functional specification, and an ABAP developer builds a custom application that must be promoted through Dev, QA, and acceptance testing before it reaches production.

These processes take days or weeks, when in reality, modern business needs require this gap to be closed in minutes.

Going through this session, you will see how the **SAP Domain Data Access Agent** solves these problems. Three different surfaces all powered by our agent will demonstrate its overarching business value.

## Surfaces

1. **Conversational Joule Platform**: business user questions spanning simple lookups to multi-view joins and whole-portfolio rankings, and the same agent reaching across more than one business system (SAP S/4HANA and SAP Ariba)
2. **A custom application**: the same underlying agent embedded inside a custom user-facing dashboard
3. **The Agents surface**: where the data agent becomes a tool that your own agent calls over A2A, reasoning over and acting on the results as a human would

## Additional Technical Takeaways

In addition to understanding the business value and integration potential of our agent for you and your customers, you will gain a better understanding of how the agent:

- Propagates and scopes authorization based on the underlying user's role grants
- Resolves and shortlists data view or entity candidates for querying
- Handles lookups, filters, aggregations, and multi-view joins for complex questions


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

- [Getting Started](exercises/ex0/): connect to the hosted service, run your first natural-language question, and open the panel to see the view the agent chose.
- [Exercise 1 - Ask your data in plain language with Joule](exercises/ex1/)
    - [Exercise 1.1 - Single-domain fluency](exercises/ex1#exercise-11---single-domain-fluency)
    - [Exercise 1.2 - Reasoning across views](exercises/ex1#exercise-12---reasoning-across-views)
    - [Exercise 1.3 - The same agent on a second system (Ariba)](exercises/ex1#exercise-13---the-same-agent-on-a-second-system-ariba)
- [Exercise 2 - A custom app on the agent](exercises/ex2/)
    - Pick a role, load a dashboard shaped for that job, and see the live call behind each tile
- [Exercise 3 - Bring your own agent](exercises/ex3/)
    - [Exercise 3.1 - Build a flow: query, reason, act](exercises/ex3#exercise-31---build-a-flow-query-reason-act)
    - [Exercise 3.2 - Design your own integration](exercises/ex3#exercise-32---design-your-own-integration)

## Contributing
Please read the [CONTRIBUTING.md](./CONTRIBUTING.md) to understand the contribution guidelines.

## Code of Conduct
Please read the [SAP Open Source Code of Conduct](https://github.com/SAP-samples/.github/blob/main/CODE_OF_CONDUCT.md).

## How to obtain support

Support for the content in this repository is available during the actual time of the online session for which this content has been designed. Otherwise, you may request support via the [Issues](../../issues) tab.

## License
Copyright (2026) SAP SE or an SAP affiliate company and teched2026-AS263 contributors. Please see our [LICENSE](LICENSE) for copyright and license information. Detailed information including third-party components and their licensing/copyright information is available [via the REUSE tool](https://api.reuse.software/info/github.com/SAP-samples/teched2026-AS263).
