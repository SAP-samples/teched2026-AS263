# Exercise 3 - A custom app on the agent (Applications)

Joule answers one question at a time. This is the other packaging: the same agent inside a custom-built app, where every tile on the screen is a live call to it. A chat box answers one question; a purpose-built screen pulls many answers together and shapes them for one person's job.

Switch to the **Applications** tab.

## Step 1 - Pick the role the app is built for

The app opens on a question: who is this app for? Pick a role and it builds the dashboard for it.

1. Under **Who is this app for?**, pick **Billing Manager**.
2. The dashboard appears, shaped for that role: contracts still to bill, unbilled by portion, and the count blocked for billing.

Each tile shows the plain-English question it asks and the label "Powered by the Domain Data Access Agent." That is the whole integration behind a tile: a question in, grounded data back. No SQL in the app, no schema, no connection code.

## Step 2 - Load a tile

Click **Load** on one tile. It fires a live call to the agent and fills with real data from the SAP system after a few seconds. The question under the tile title is exactly what it sent.

## Step 3 - Load all tiles

Click **Load all tiles** (top right). Each tile fires its own call and fills in. Now one screen is doing real work at once: a worklist a billing manager acts on, a breakdown they read, a headline number they watch. No single chat answer gives you that; the app does, because it fires several agent calls and lays the results out together.

## Step 4 - Switch the role

Pick a different role (for example **Operations Lead** or **Clarification Case Processor**). The dashboard rebuilds for that role, each tile still a live call. Notice the same question can serve more than one role's dashboard, and that you never wrote a query, wired a data source, or touched a schema. You picked who the app is for, and the agent answered for them.

Continue to - [Exercise 4 - Bring your own agent (Agents)](../ex4/README.md)
