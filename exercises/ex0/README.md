# Getting Started

In this exercise you connect to the hosted Domain Data Access Agent and confirm it answers a natural-language question. That gives you a baseline for everything that follows.

## What you are connecting to

The Domain Data Access Agent is available as a hosted service for this session. You do not install anything or join any network. You reach it over normal internet, and the presenter shares the credentials live.

<!-- TODO(Evan): conceptual architecture diagram here (question -> agent -> Domain Model -> SAP data). No internal hosting/infra detail. Replace placeholder image below. -->
<br>![AS263 architecture](images/00_00_0010.png)

## Step 1 - Open the service

1. In Chrome or Edge, open the service URL the presenter gives you:
   `TODO(Evan): attendee-facing URL (shared at the session)`
2. When prompted, enter the credentials the presenter shares during the session.
   <!-- TODO(Evan): confirm the sign-in step attendees see, kept generic. -->

> If you cannot reach the URL, check that you have a working internet connection. The TechEd guest Wi-Fi is fine. If it still fails, flag a presenter.

## Step 2 - Run your first question

1. In the question box, enter:
   > `TODO(Evan): a known-good S/4HANA question that has backing data on the deployed service, e.g. "What were the top 5 cost centers by actual spend last quarter?"`
2. Submit, and wait for the agent to respond.

You should get a direct answer back, usually a table or a short result. If you expand the detail, you will also see the SQL and the SAP views the agent chose. You never gave it the schema. It worked that out from the Domain Model.

## Summary

You are connected to the data-access agent and have seen one natural-language question answered end to end. Next you will push it across multiple domains.

Continue to - [Exercise 1 - Natural-language data access with the Agent Simulator](../ex1/README.md)
