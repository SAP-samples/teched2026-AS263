# Exercise 2 - Build a custom app on the agent

Exercise 1 used Joule: a chat box that answers one question at a time. That is how an end user reaches the Domain Data Access Agent. This exercise is how a *developer* reaches it. You build a small custom application whose every widget is a live call to the same agent.

The point is composition. A chat box answers one question; a purpose-built screen composes many answers into one workflow. Here you assemble that screen yourself.

Switch to the **Custom Applications** tab. You start with an empty canvas.

## Exercise 2.1 - Add your first widget

1. Click **Add a widget**.
2. Pick a question for the agent to answer. Start with:
   > `Count clarification cases by processing status`
3. Choose how to show it. For a question that returns counts, **KPI tiles** is a good fit.
4. Click **Add to dashboard**.

The widget appears and runs a live call to the Domain Data Access Agent. After a few seconds it fills with real data from the SAP system. You picked the question and the presentation; the agent did the rest.

## Exercise 2.2 - Compose a dashboard

One widget is not an app. Add two more so the screen does real work:

1. Add **`Show me the top 5 clarification cases I should resolve first`** as a **Table / worklist**. This is the operational list a processor acts on.
2. Add **`Why are utilities contracts blocked for billing?`** as a **Bar breakdown**. This is the analytical view a billing manager needs.

You now have three widgets on one screen: a KPI summary, an actionable worklist, and an analytical breakdown. No single chat answer gives you that. A custom app does, because it fires several agent calls and lays the results out together.

## Exercise 2.3 - See the call behind a widget

Every widget is one agent call. Prove it to yourself.

1. On any widget, click **call**.
2. Read the request. It is a single `message/send` call to the agent with your plain-English question. That is the entire integration: a question in, grounded data back.
3. Note what you did *not* write: no SQL, no schema, no connection code. The widget is a thin shell around one agent call.

## Exercise 2.4 - Try your own composition

1. Remove a widget (the small close control on its header), or add another from the question list.
2. Try the **same question in a different shape**. For example, add `Why are utilities contracts blocked for billing?` as **KPI tiles** instead of a breakdown.
3. Notice the data is identical; only your presentation changed. The agent returns grounded data, and you decide how your app shows it.

## Summary

You have built a custom application on the Domain Data Access Agent: you chose the questions, chose the layout, and every widget ran a live call. That is the developer's path to the same capability Joule gave your users. Next you will reach the agent a third way, from an agent of your own.

Continue to - [Exercise 3 - Bring your own agent](../ex3/README.md)
