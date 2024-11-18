DocProStar processes are made up of activities connected by routes. These routes typically connect 2 activities to each other, but can also connect an activity to more than one destination using gateways and conditions. 

## Route Properties

Routes have up to three properties in the General section.

- **Label**

- **Expiration Date Factor**

This setting allows to influence the expiration date. A factor between 0 and 1 sets the expiration date closer to the creation date of the work item. A factor above 1 extends the expiration date to be further in the future. 

>[!example]
>Take a creation datetime of 10:00 and expiration date of 20:00, on the same day.
*A value of 0.3 changes the expiration to 13:00: 10:00 + (20:00 - 10:00) * 0.3 == 13:00.
*A value of 1.3 changes the expiration to 23:00: 10:00 + (20:00 - 10:00) * 1.3 == 23:00.

- **Condition** 

Only on conditional routes after a Gateway. Defines under what condition that route is taken.

## Gateways

A gateway is a connection from one activity to two or more destination activities. To visually highlight conditional routes those are displayed showing a route into a rhombus from there several routes are connected to several activities.

The default route defines the connection that is taken if none of the other connections matches the condition. If a route connects two activities only, this one-to-one route is always considered as the default route. If an activity is connected to more than one destination activity this route is a gateway. For each outgoing connection you need to configure a condition in the route properties of the settings panel. If the conditions meets for a work item this route is used for the process flow. If a work item does not meet any of the configured conditions, the process uses the default route. A default route is displayed with a little stroke near the gateway. Connections that have not configured the conditions on the Process tab are marked with ![red cross](https://localhost/processmodeler/assets/help/img/icons/red_cross_24.png "Route has no conditions configured yet."). A route that has a condition configured is displayed in black.

To set the condition for a route, select the outgoing route and enter a condition for the **Condition** text field in the General area of the settings panel.

![[Pasted image 20241003183858.png]]

## Conditional Activities

When an activity is connected to more than one destination activity, you need to specify conditions when a certain route to take. For example, after documents are imported into the system, image files are processed by the “image classifier” whereas text documents are processed by the “content classifier”. To specify the condition, select the route and enter a condition into the **Condition** field that is provided in the General area on the **Route properties** tab in the settings panel.

Besides the conditions for routes, you can also specify conditions for an activity instance such as when you want to process all imported documents with a “content classifier” that determines different document types as result of the document's content. 

For loaded image documents, you have to perform text recognition (OCR) prior to analyzing the content. That means that an activity that performs OCR does not need to process text documents but image documents only. So, you can specify a condition for this activity to process work items that reference image documents only. You enter the condition for an activity by selecting the activity in the process diagram and entering the condition into the **Activity filter** field within the **x2 conditions** area on the **Process** tab in the settings panel.

![[Pasted image 20241003183937.png]]

To evaluate the routing conditions the system converts the expression into an abstract syntax tree. In addition, it no longer performs type castings so that expressions that try to evaluate "55" == 55 now fail.

How you specify a condition depends on the field type. For example, for a string field you have to use quotes in the equation. For more information about text, typed, and captured values, see the [[Field Types, Values and Indexed Fields]] and [[Field Evaluation Methods]] articles.

