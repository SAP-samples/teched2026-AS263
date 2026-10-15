# Exercise 2 - A custom app on the agent

Exercise 1 used Joule: a chat box that answers one question at a time. That is how an end user reaches the Domain Data Access Agent. This exercise is the developer's path. The same agent sits inside a custom-built application, and every tile on the screen is a live call to it.

The point is composition. A chat box answers one question. A purpose-built screen pulls many answers together and shapes them for one person's job. Here that screen is already built, and you drive it.

Switch to the **Applications** tab.

## Exercise 2.1 - Pick a role

The app does not open on a blank dashboard. It opens on a question: who is this app for? Pick a role and the app builds the dashboard for it.

1. Under **Who is this app for?**, pick **Billing Manager**.
2. The dashboard appears, shaped for that role: the contracts still to bill, a breakdown of unbilled contracts by portion, and the count blocked for billing.

Nothing about the agent changed from Exercise 1. The same Domain Data Access Agent answers each tile. What changed is the packaging: a screen built for one job instead of a chat box.

## Exercise 2.2 - Load the tiles

1. Click **Load all tiles** (top right of the dashboard).
2. Each tile fires its own live call to the agent and fills with real data from the SAP system after a few seconds.

You now have one screen doing real work: a worklist a billing manager acts on, a breakdown they read, and a headline number they watch. No single chat answer gives you that. A custom app does, because it fires several agent calls and lays the results out together.

## Exercise 2.3 - See the call behind a tile

Every tile is one agent call, nothing more.

1. Read the label under each tile title: "Powered by the Domain Data Access Agent."
2. That is the whole integration behind the tile: a plain-English question in, grounded data back. No SQL in the app, no schema, no connection code. The tile is a thin shell around one agent call.

## Exercise 2.4 - Switch the role

The dashboard is built from the role, so changing the role rebuilds it.

1. Pick a different persona (**Clarification Case Processor** or **Operations Lead**).
2. The tiles change to the ones that role needs, each still a live call.
3. Notice what you did not do: you did not write a query, wire a data source, or touch a schema. You picked who the app is for, and the agent answered for them.

## Summary

You drove a custom application on the Domain Data Access Agent: you picked the role, the app shaped a dashboard for it, and every tile ran a live call. That is the developer's path to the same capability Joule gave your users. Next you reach the agent a third way, from an agent of your own.

Continue to - [Exercise 3 - Bring your own agent](../ex3/README.md)
