# System Architecture Case Study

At Kuala Tech, we build enterprise level systems that are excellently designed,
robust, flexible, extensible, and secure. For that reason, we place heavy emphasis
on system architecture and would like to get an understanding of how you would
design a system given requirements in a business domain.

    You do not need to write code for your answer. Though, you can use pseudocode to highlight your preferred method of executing the given task. Feel free to make use of any design patterns you are familiar with.

## Task

You have recently been promoted to be the team lead for a brand-new engineering team
in your company, the *payments and subscriptions* team. As this is a new area for
you, you diligently organize time with experts in the department to discuss the
basics of the ***domain*** and how it works. Here is their response:

> “When a *lead* uses our app for the first time, they must pick one of three
*subscription plans*. These are *basic*, *premium*, and *exclusive*. Depending on
which they pick determines which *features* they get access to within the app. This
may change over time. Once a *subscription plan* has been created, we consider that
the *lead* has converted to a *customer*, and we call them a *customer* until they
*churn*. At this point, we call them a *lead* again. After 6 months, we call them a
*lost lead* and we might target them with a *re-engagement campaign*, which could
include a *discount code*. Once a *plan* is created, we set up a *recurring payment*
to *capture funds* from the *customer* by *direct debit*.”

Excitedly, you run off and define a few interfaces as a starting point for the new
application your team will be building. What are those interfaces?
