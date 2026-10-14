# Exercise 2 - The same agent on a real customer problem

Exercise 1 showed the agent answering questions in Joule. Nothing about the agent changes here. This exercise shows it the way a customer actually uses it, framed around a real Forward-Deployed Engineering engagement in the Utilities domain. You watch the agent drive a business workflow end to end instead of answering one-off questions.

Switch to the **Utilities scenario** tab. The scenario runs in three acts down the left rail. Work them in order.

## Scenario

A clarification-case processor at a Utilities-domain customer starts every morning with the same manual ritual: opening several Fiori apps, scrolling through billing-exception queues, and copying case IDs into a spreadsheet to work out what to tackle first.

With the Domain Data Access Agent in Joule, that same processor asks natural-language questions against live S/4HANA data, in English or German, and gets the prioritised exception list back in one conversational turn. The three acts below follow one processor through a real morning: triage the open cases, find out what is blocking billing, and hand a structured list to a supervised fix.

## Act 1 - Triage open exceptions

What needs my attention today?

1. > `List the open clarification cases`
   The processor's first question every morning. Open the panel and note the view the agent resolved for billing-exception cases.
2. > `Show me the top 5 clarification cases I should resolve first`
   The agent applies the prioritisation rule (urgency and due date), not you. You asked for "the ones I should resolve first" and it worked out what that means.

## Act 2 - Billing blockers

Why are contracts stuck?

1. > `List blocked utilities contracts to be billed`
   The question moves from exception cases to billing objects. The agent picks the right view for the new subject on its own.
2. > `Why are utilities contracts blocked for billing?`
   This turns a raw list into a summary: the agent groups the blocked contracts by block reason, which is what a billing manager actually needs to act.

## Act 3 - Portfolio overview

How big is the backlog?

1. > `Count clarification cases by processing status`
   A cross-cutting status breakdown for the team lead, with no custom report and no BI tool.

## Act 1, in German

The agent resolves intent, not language. A German utility's processor would ask the same first question in German:

1. > `Zeige mir die offenen Klärungsfälle`
2. Open the panel and confirm the agent resolved the same billing-exception view it used for the English question in Act 1. The language changed; the answer did not.

## Now you try

1. Take any question above and change one thing: a filter, a grouping, or the ordering. For example, ask for cases by priority instead of by status.
2. Confirm the agent adapts with no schema input from you.

## Where this goes - supervised remediation

The exception list the agent returns is not the end. It is the input to a human-approved fix.

A remediation agent proposes a correction for each case. The processor reviews the proposal, approves or edits it, and the fix is written back to S/4HANA only after human sign-off. That closes the loop: natural-language query in, structured exception list, supervised fix, system update. The data-access agent is the grounded first step of that loop, and in the next exercise you see it offered as a tool any agent can build on.

## Summary

You have watched the Domain Data Access Agent carry a real customer investigation across three acts, in two languages, driven entirely in plain language. Next you will call that same capability from an agent of your own.

Continue to - [Exercise 3 - Bring your own agent](../ex3/README.md)
