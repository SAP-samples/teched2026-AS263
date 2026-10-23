# Exercise 2 - Ask your data in plain language (Joule)

Joule is the surface your users already know: a plain chat box. You sign in as a business role, pick a question, and behind the chat the Domain Data Access Agent runs a live query against real SAP data and hands back rows. No SQL, no transaction code, no schema knowledge.

You run verified questions as suggestion chips here; free-form questions are reserved for Freestyle. This exercise is about range: one agent, many roles, more than one SAP system.

Open the **Joule** tab.

## Step 1 - Connect the dots: see what is underneath

Click **Show system diagram** in the tab bar. It lays out the pieces:

> You -> SAP IAS (authenticate) -> Joule -> principal propagation -> Domain Data Access Agent -> SAP S/4HANA / Ariba

Joule is the chat surface; the Domain Data Access Agent is the engine underneath doing the resolve, generate, and execute work you watched in the Simulator. Your identity is propagated through, so every query runs with your own authorizations. Leave the diagram open; it animates as a question runs.

## Step 2 - Sign in through SAP IAS

The Joule tab opens on an SAP Identity Authentication sign-in, the same first hop you just saw in the diagram. Instead of a password, you pick who you are from a short list of business users:

- **Emma Ellis**, Internal Sales Representative
- **Claire Corbett**, Finance Controller
- **Evan Eldridge**, Master Data Specialist
- **Dana Delaney**, Maintenance Technician

Pick **Emma Ellis** and click **Continue**. You land in the Joule chat signed in as that user. The questions you can run are the ones that fit her role, because the agent scopes to the authorizations she signs in with. This is the governance funnel from the Simulator, now from the user's own seat.

## Step 3 - Ask a question

The questions for your role appear as buttons above the chat box. The chat box is there, but you do not type in it: click a question and it fills the box, then press **Send**. As **Emma Ellis**, run the lookup:

> `when the sales order 140780 was created`

Then the cross-document question:

> `show me the delivery document details and the invoice details which are related to sales order 140780`

The second one needs more than one business view joined (the order, its delivery, its invoice). You asked once; the agent planned the join. This is the sales rep scenario from the workshop intro, answered in seconds.

## Step 4 - Read the generated query

On an answer, open **Show SQL** and read the query the agent generated and ran. You never wrote it and never named the views in it.

## Step 5 - Sign in as a different role

Click **Sign out** on the signed-in strip to return to the SAP IAS screen, then sign in as a different user to see the same agent serve a different job:

- As **Evan Eldridge** (Master Data Specialist): `tell me the name of business partner 1003286`, then `Search business partners with city Shanghai`.
- As **Dana Delaney** (Maintenance Technician): `List all jobs for plant 1010`, then `Show me all jobs currently in process`.
- As **Claire Corbett** (Finance Controller): `Show general ledger entries for company code 1710`.

Each role signs in fresh and sees only its own questions. Master data, maintenance, finance: one agent, each user scoped to their own authorizations.

## Step 6 - Cross to a second system (Ariba)

Everything so far hit SAP S/4HANA. Switch to the **SAP Ariba** tab at the top. Because Ariba is a different system, you sign in again through SAP IAS, this time as an Ariba user (**Sofia Mertens**, Sourcing Manager). Sign in and run:

> `List all sourcing projects`

Same chat, same way of asking, a different SAP system underneath, and its own sign-in. A business user does not need to know whether sourcing projects live in Ariba or sales orders live in S/4HANA. They ask, and the agent reaches the right system.

Continue to - [Exercise 3 - A custom app on the agent (Applications)](../ex3/README.md)
