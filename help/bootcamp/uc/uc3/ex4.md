---
title: Bootcamp - Blending physical and digital - Journey Optimizer Create your journey
description: Bootcamp - Blending physical and digital - Journey Optimizer Create your journey
kt: 5342
audience: developer
doc-type: tutorial
activity: develop
exl-id: be8c23ec-c5f8-4abc-849f-994446072a84
---
# 3.4 Create your journey

In this exercise, you'll configure the journey that needs to be triggered when someone creates an account on the demo website.

Login to Adobe Journey Optimizer by going to [Adobe Experience Cloud](https://experience.adobe.com). Click **Journey Optimizer**.

![ACOP](./images/acophome.png)

You'll be redirected to the **Home**  view in Journey Optimizer. First, make sure you're using the correct sandbox. The sandbox to use is called `Bootcamp`. To change from one sandbox to another, click on **Prod** and select the sandbox from the list. In this example, the sandbox is named **Bootcamp**. You'll then be in the **Home** view of your sandbox `Bootcamp`.

![ACOP](./images/acoptriglp.png)

In the left menu, click **Journeys**. Next, click **Create Journey** to create a new journey.

![ACOP](./images/createjourney.png)

You'll then see an empty journey screen.

![ACOP](./images/journeyempty.png)

In the previous exercise, you created a new **Event**. You named it like this `yourLastNameBeaconEntryEvent` and replaced `yourLastName` with your last name. This was the result of the Event creation:

![ACOP](./images/eventdone.png)

You now need to take this event as the start of this Journey. You can do this by going to the left side of your screen and searching for your event in the list of events.

![ACOP](./images/eventlist.png)

Select your event, drag and drop it on the journey canvas. Your journey now looks like this. Click **Ok** to save your changes.

![ACOP](./images/journeyevent.png)

As the second step in the journey, you need to add a **Message** action. Go to the left side of your screen to **Actions**, select the **Message** action, then drag and drop it on the second node in your journey.

![ACOP](./images/journeyactions.png)

On the right side of your screen, you now need to select the push notification. Click the **Edit** icon.

![ACOP](./images/emptymsg.png)

You'll then see the **Select a message** popup. In that list, you need to select the template with the name `yourLastName - Beacon Entry Push Notification`. Click **Select**.

![ACOP](./images/emailmsglist.png)

You'll then see this. The message you created earlier is now connected to this journey. After adding a message in a journey, you can take the journey context and add it to your push notification template. To do that, click **Open the message**.

![ACOP](./images/jomsg1.png)

You'll then see that your message is opened in a new window. Click the **Body** text area again.

![ACOP](./images/jomsg2.png)

Click **Contextual Attributes** and then **Journey Orchestration**.

![ACOP](./images/jomsg3.png)

Click **Events**.

![ACOP](./images/jomsg4.png)

Click **Events**.

![ACOP](./images/jomsg5.png)

Click **Place context**.

![ACOP](./images/jomsg6.png)

Click **POI Interaction**.

![ACOP](./images/jomsg7.png)

Click **POI Detail**.

![ACOP](./images/jomsg8.png)

Click the **+** icon on **POI Name**.

![ACOP](./images/jomsg9.png)

You'll then see this. Click **Save**.

![ACOP](./images/jomsg10.png)

Your message is now ready. Click **Publish**.

![ACOP](./images/jomsg11.png)

Click **Publish** again.

![ACOP](./images/jomsg12.png)

Once your message is published, you can go back to your other browser window, which contains your journey.

![ACOP](./images/jomsg13.png)

Click **Ok**.

![ACOP](./images/jomsg14.png)

As the third step in the journey, you need to add a **sendMessageToScreen** action. Go to the left side of your screen to **Actions**, select the **sendMessageToScreen** action, then drag and drop it on the third node in your journey. You'll then see this.

![ACOP](./images/jomsg15.png)

The **sendMessageToScreen** action is a custom action that will publish a message to the endpoint that is used by the in-store display. The **sendMessageToScreen** action expects a number of variables to be defined. You can see those variables by scrolling down until you see **Action Parameters**.

![ACOP](./images/jomsg16.png)

You now need to set the values for every action parameter. Follow this table to understand what values are required where.

| Parameter     | value       |
|:-------------:| :---------------:|
|DELIVERY|`'image'`|
|ECID|`@{yourLastNameBeaconEntryEvent._experienceplatform.identification.core.ecid}`|
|FIRST NAME |`#{ExperiencePlatform.ProfileFieldGroup.profile.person.name.firstName}`|
|EVENTSUBJECT|`#{ExperiencePlatform.ProductListItems.experienceevent.first(currentDataPackField.eventType == "commerce.productViews").productListItems.first().name}`|
| EVENTSUBJECTURL |`#{ExperiencePlatform.ProductListItems.experienceevent.first(currentDataPackField.eventType == "commerce.productViews").productListItems.first()._experienceplatform.core.imageURL}`|
| SANDBOX         |`'bootcamp'` |
| CONTAINERID         | `''` |
| ACTIVITYID         |`''` |
| PLACEMENTID         | `''` |

{style="table-layout:auto"}

To set those values, click the **Edit** icon.

![ACOP](./images/jomsg17.png)

Next, select **Advanced Mode**.

![ACOP](./images/jomsg18.png)

Then, paste the value based on the table above. Click **Ok**.

![ACOP](./images/jomsg19.png)

Repeat this process to add values for each field.

>[!IMPORTANT]
>
>For the field ECID, there's a reference to the event `yourLastNameBeaconEntryEvent`. Please ensure to replace `yourLastName` by your last name.

The end result should look like this:

![ACOP](./images/jomsg20.png)

Scroll up and click **Ok**.

![ACOP](./images/jomsg21.png)

Let's add an orchestration event to **End** the Journey. In the left side of the screen, go to **Orchestration** and select **End**. Drag and Drop this onto the 3rd step of the journey. Click **Ok**.

![ACOP](./images/orch.png)

You still need to give your journey a Name. You can do that by clicking the **Properties** icon in the top right side of your screen.

![ACOP](./images/journeyname.png)

You can then enter the journey's name here. Please use `yourLastName - Beacon Entry Journey`. Click **OK** to save your changes.

![ACOP](./images/journeyname1.png)

You can now publish your journey by clicking **Publish**.

![ACOP](./images/publishjourney.png)

Click **Publish** again.

![ACOP](./images/publish1.png)

You'll then see a green confirmation bar saying that your Journey is now Published.

![ACOP](./images/published.png)

Your journey is now live and can be triggered. 

You've now finished this exercise.

Next Step: [3.5 Test your journey](./ex5.md)

[Go Back to User Flow 3](./uc3.md)

[Go Back to All Modules](../../overview.md)
