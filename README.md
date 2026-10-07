# AS263 - Powering autonomous agents with natural language data access

## Description

This repository contains the material for the SAP TechEd 2026 session **AS263 - Powering autonomous agents with natural language data access**.

An agent is only as useful as the data it can reach. Right now, getting an agent to answer a real business question ("which cost centers went over budget last quarter?", "which suppliers have the longest payment terms?") means someone has to know the schema, write the SQL, and wire up the joins first. This session shows how an autonomous agent closes that gap: you ask in plain English, and the agent works out which business entities and views it needs across one or more domains, writes the query, and returns a grounded answer. The user never has to know the schema. Under the hood this leverages proprietary metadata enriched by SAP Domain Models, which is what lets the agent map your question to the right data.

Over about two hours you will drive the same capability through three different surfaces, so you can see that the work is being done by the agent and not by a scripted demo:

1. Joule, the SAP assistant your users already know, as a plain chat box over your SAP data.
2. A real customer scenario, the capability applied to a Utilities-domain FDE problem.
3. The Agent surface, where the same capability becomes a tool your own agent can call.

## Overview

By the end of this session you will be able to:

- Ask business questions in plain English from inside Joule and get back grounded, correct answers over real SAP data in the S/4HANA and Ariba domains.
- Watch the agent answer a cross-domain question that joins two domains, which a single hardcoded query cannot do.
- See the same agent carry a real customer investigation end to end in a Utilities-domain FDE scenario.
- Call that same capability from an agent of your own, as a governed data-access tool.
- Understand how the agent leverages proprietary metadata enriched by SAP Domain Models under the hood to map plain-English questions to the right data.

<!-- TODO(Evan): one architecture diagram here, at the level of detail cleared for a
     public repo. Keep it conceptual (question -> agent -> Domain Model -> SAP data).
     Do NOT show internal hosting/infra. Replace exercises/ex0/images placeholder. -->

## Requirements

The exercises run over the public internet against a hosted service. There is nothing to install, and no VPN or special network access is required. On the hands-on laptop (or your own) you need:

- A current browser (Chrome or Edge).
- Access credentials for the hosted Domain Data Access Agent service. The presenter hands these out during the session, which is why they are not published in this repository. <!-- TODO(Evan): confirm cred format and the live hand-out mechanism. Keep both out of the repo. -->

> **A note on access.** The Domain Data Access Agent is available as a hosted service for this session. You reach it over the public internet, and the presenter shares the credentials you need during the session.
> Service URL: `TODO(Evan): fill in the attendee-facing URL` (shared at the session).

## Exercises

- [Getting Started](exercises/ex0/): connect to the hosted service and run your first natural-language question.
- [Exercise 1 - Ask your data in plain language with Joule](exercises/ex1/)
    - [Exercise 1.1 - Ask a question over the S/4HANA domain](exercises/ex1#exercise-11--ask-a-question-over-the-s4hana-domain)
    - [Exercise 1.2 - Same agent, a different domain (Ariba)](exercises/ex1#exercise-12--same-agent-a-different-domain-ariba)
    - [Exercise 1.3 - A cross-domain question](exercises/ex1#exercise-13--a-cross-domain-question)
- [Exercise 2 - The same agent on a real customer problem](exercises/ex2/)
- [Exercise 3 - Bring your own agent](exercises/ex3/)
    - [Exercise 3.1 - Watch the tool call](exercises/ex3#exercise-31--watch-the-tool-call)
    - [Exercise 3.2 - Ask your own question](exercises/ex3#exercise-32--ask-your-own-question)

## Contributing
Please read the [CONTRIBUTING.md](./CONTRIBUTING.md) to understand the contribution guidelines.

## Code of Conduct
Please read the [SAP Open Source Code of Conduct](https://github.com/SAP-samples/.github/blob/main/CODE_OF_CONDUCT.md).

## How to obtain support

Support for the content in this repository is available during the actual time of the online session for which this content has been designed. Otherwise, you may request support via the [Issues](../../issues) tab.

## License
Copyright (2026) SAP SE or an SAP affiliate company and teched2026-AS263 contributors. Please see our [LICENSE](LICENSE) for copyright and license information. Detailed information including third-party components and their licensing/copyright information is available [via the REUSE tool](https://api.reuse.software/info/github.com/SAP-samples/teched2026-AS263).
