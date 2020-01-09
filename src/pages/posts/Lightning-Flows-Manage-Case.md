---
title: Manage your case on clicks! - Lightning Flows
excerpt: In a fast phase workstyle, we need to do our work just on clicks with more
  efficiency. Salesforce provides you the best platform to manage your cases just
  on a few clicks using **Lightning Flows**.
img_path: "/images/Flows.PNG"
post_button_label: Read More
date: 2017-04-02T18:30:00Z
template: page
subtitle: ''

---
**Introduction**

In a fast phase workstyle, we need to do our work just on clicks with more efficiency. Salesforce provides you the best platform to manage your cases just on a few clicks using **Lightning Flows**.

Salesforce provides you **Lightning Flows** which helps to manage your work just on clicks, **Lightning Flows** provides you an easy playground where you can build some flow diagram and use them on your records.

In flow you can use Apex, Lightning Components and also helps you to create, update and delete your records just on click.

**Use Case**

Starting with a use case where a product based company is managing its Cases.

When a customer submits a case to the company, according to its record type system suggests a few steps follow/manage the case. Some steps can be dependent, few can be optional and required for managing the case.

When a company’s representative opens the record a lightning component will help him to complete the masonry steps on case to close the case.

**Implementation**

Implementing the use case, where we will use a few objects, metadata for configuration using flows we and its playground we can easily set up all the flows, here we start.

Object Relationship

![](/images/Object Flow Diagram.jpeg)

**Case Plan Object**

1. Name
2. Record Type (Case Record Type Name)
3. Status (New, In Progress, Completed)

This object will be used for maintaining a proper plan for each Case Record Type, where only one Case Plan will be active at a time and associated it with Case Record Type using Metadata.

**Case Step Object**

1. Name (Unique)
2. Action (Flow Name)
3. Case Plan (MD)
4. Associated Case (Lookup)
5. Status (New, In Progress, Completed).
6. Required. (Checkbox)
7. Dependent Case Step (Text Name of Case Step).

Case Step Object used for adding action, like users want to send an Acknowledgement to a customer that ‘your logged case is in progress’. System Admin will create a flow/workflow and add its API Name to the case step Action field.

**Case Object**

1. Add a custom field associated Case Plan (Lookup To Case Plan).

Whenever a case record is created, trigger fired and add active Case Plan id to associated Case Plan field on Case object from metadata.

**Create a Metadata - To maintain uniqueness of Case Plan on each case record.**

1. Active Case Plan Id.
2. Record Type.

**Create Case Plan Flow**

Create a Lightning flow that helps you to edit and insert a new Case Plan and this case plan flow will fire another flow which will help you to add Case Steps to your Case Plan and each case steps have their action.

![](/images/Create Case Plan.png)

**Create a Lightning Component that provides you the UI of your application.**

![](/images/lc.PNG)

Each button is associated with its Case Step, so when user clicks on the button an action flow is fired using <lightning: flow>.

In flow you have to check its status if it is 'In Progress', you need to complete manual action if it is an automated flow it will be fired automatically and update the status of Case Step as well according to flow diagram.

![](/images/Managing Case Steps.png)

The diagram below shows the detailed functionality of the component.

![](/images/Product Case Management Final.png)

**Future Scope**

In the future we can also provide:

1. Feedback System after closing case.
2. Live updates for customer’s problems.
3. Automated assigned cases as per the company representative’s skill set.
4. Provide community to end-users and give them a flow which helps them to log a case with some suggestions and predictions.

**Other Resources.**

[Lightning Flows Trailhead](https://trailhead.salesforce.com/en/content/learn/modules/business_process_automation)

[How to add flows in Lightning Component](https://developer.salesforce.com/docs/component-library/bundle/lightning:flow/example)

[Lightning Component](https://developer.salesforce.com/docs/atlas.en-us.lightning.meta/lightning/intro_framework.htm)