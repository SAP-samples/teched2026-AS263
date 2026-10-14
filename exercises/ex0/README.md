# Getting Started

In this exercise you connect to the hosted Domain Data Access Agent and run your first natural-language question. By the end you will have a baseline for everything that follows, and you will have seen the one idea this whole session rests on: you ask in plain English, and the agent works out the data for itself.

## What you are connecting to

The Domain Data Access Agent is available as a hosted service for this session. You do not install anything and you do not join any network. You reach it over normal internet, and the presenter shares the credentials live.

The service puts the same capability behind three surfaces, shown as tabs across the top:

- **Joule** - the SAP assistant, as a plain chat box over your SAP data.
- **Utilities scenario** - the same agent driving a real customer workflow.
- **Agent** - the same capability as a tool your own agent can call.

You will work through all three. For now, stay on **Joule**.

## Step 1 - Open the service

1. In Chrome or Edge, open the service URL the presenter gives you:
   > `[Presenter fills in live: attendee-facing service URL]`
2. When prompted, enter the credentials the presenter shares during the session.

> If you cannot reach the URL, check that you have a working internet connection. The TechEd guest Wi-Fi is fine. If it still fails, flag a presenter.

## Step 2 - Run your first question

1. Make sure you are on the **Joule** tab.
2. In the question box, pick the suggested question or type:
   > `Show me all open sales orders`
3. Submit, and wait for the agent to respond.

You get a direct answer back, a short table of sales orders. You never told the agent which table, which view, or which columns. It worked that out on its own.

## Step 3 - Look at what the agent chose

This is the part most demos skip, and it is the part that proves the point. Open the detail on that answer (the SQL / execution panel) and look at the query the agent ran.

1. Find the SQL the agent generated.
2. Find the one SAP view it selected: `C_OpenSalesOrder`.
3. Note that you never named it. You asked for "open sales orders" in plain English, and the agent mapped that to the right business view on its own, using the Domain Model underneath.

> Keep this panel in mind. Through the rest of the session, every time the agent answers, you can open this view and see exactly which data it reached for. That is how you tell real data access from a scripted demo.

## Summary

You are connected to the Domain Data Access Agent, you have run one natural-language question end to end, and you have seen the agent pick the right SAP view with no schema input from you. Next you will push it across more question shapes and watch how it holds up.

Continue to - [Exercise 1 - Ask your data in plain language with Joule](../ex1/README.md)
