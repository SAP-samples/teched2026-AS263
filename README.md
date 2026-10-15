# AS263 - Powering autonomous agents with natural language data access

## Description

This repository contains the material for the SAP TechEd 2026 session **AS263 - Powering autonomous agents with natural language data access**.

An agent is only as useful as the data it can reach. Right now, getting an agent to answer a real business question ("which sales orders are blocked from delivery?", "why are these contracts blocked for billing?") means someone has to know the schema, write the SQL, and wire up the joins first. This session shows how an autonomous agent closes that gap: you ask in plain English, and the agent works out which business entities and views it needs, writes the query, and returns a grounded answer. The user never has to know the schema. Under the hood this leverages proprietary metadata enriched by SAP Domain Models, which is what lets the agent map your question to the right data.

The session has two halves. In the first, you drive the capability yourself to understand what it does and prove it is real. In the second, you look at it as a tool and work out how you would wire it into an agent of your own. You reach the same capability through three surfaces, and each one shows something the others cannot:

1. **Joule**, the SAP assistant your users already know, as a plain chat box. This is where you see range: simple lookups through to multi-view joins and whole-portfolio rankings, and the same agent reaching across more than one business system (S/4HANA and Ariba).
2. **A custom application**, where the same agent is embedded in a role-shaped dashboard and every tile is a live call.
3. **The Agents surface**, where the data agent becomes a tool your own agent calls over A2A, then reasons over and acts on the result.

This is hands-on. You drive each surface yourself: ask your own questions in Joule, load a role's dashboard, and build an agent flow of your own. That is what separates real data access from a scripted demo.

## Overview

By the end of this session you will be able to:

- Ask business questions in plain English from inside Joule and get back grounded answers over real SAP data, and open the panel to see which views the agent chose.
- Watch the agent handle lookups, filters, aggregations, and multi-view joins that a single hardcoded query cannot fake, and reach across two business systems (S/4HANA sales, Ariba sourcing and contracts) from the same chat.
- Load a role-shaped dashboard in a custom application and see the single live call behind each tile.
- Build a short agent flow that queries the data agent over A2A, then reasons over and acts on the grounded result, and reason about how you would wire that into your own agent.
- Explain how the agent leverages proprietary metadata enriched by SAP Domain Models under the hood to map plain-English questions to the right data.

## Requirements

The exercises run over the public internet against a hosted service. There is nothing to install, and no VPN or special network access is required. On the hands-on laptop (or your own) you need:

- A current browser (Chrome or Edge).
- Access credentials will be provided by the presenters during the session.

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
