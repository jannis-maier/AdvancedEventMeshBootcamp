## Exercise 3: Incremental growth: Add web application as additional consumer


The publish-subscribe pattern decouples the sending and receiving applications. This makes it easy to add new applications allows for incremental growth. In this exercise a web application is added as additional consumer. The web application is subscribed to a queue and lists all business partners.

## Exercise 3.1: Create new queue for additional application

1. Go back to the original tab in your browser and click on **"Cluster Manager"** on the left.
2. In the All Services screen click on the **"Broker Asia"** tile.

HINT: If you cannot see the tiles, uncheck the "Only show my services" box.

![](./images/ex3-1.png)  


3. Switch to **"Manage"** tab and click on the **"Queues""** tile. A new window opens up.

![Pic](./images/ex3-2.png)

4. Search for the queue you created in exercise 1.2: User_**XXX** (replace **XXX** with your user number).
5. Select the checkbox on the left and press "**Action**" -> "**Clone**"

![Pic](./images/ex3-3.png)

6. Change the "Queue Name" to: **User_XXX_WebApp** (replace **XXX** with your user number). Select the checkbox to cole the subscription. Press "**Apply**".
![Pic](./images/ex3-4.png)


## Exercise 3.2: Configure Web Application
In this exercise you will conifugre the Business Partner Web Application. On this Website you will subscribe to the queue creatd in exercise 3.1 via your web browser. Every business partner published to your queue will be shown on the website.


1. Open the [Business Partner Web Applicaiton](https://sap-cpisuite-europe-01n-cpisuite-europe-01-aem-demo-client.cfapps.eu10.hana.ondemand.com/app/index.html).

2. Provide the password captured in [Exercise 1.4 - Send an event from the Try Me! Tool to your Topic](../ex1#exercise-14---send-an-event-from-the-try-me-tool-to-your-topic)

3. Fill in the queue name created in exercise 3.1: **User_XXX_WebApp** (replace **XXX** with your user number). Press **"Connect"**.
![Pic](./images/ex3-5.png)

4. The Pop-Up should close and status shows **"Connected"**. Now your browser is directly subscribed to the queue and ready to receive business partner events.
![Pic](./images/ex3-6.png)


## Exercise 3.3: Publish event to topic

In exercise 1, we did publish event to a queue. This time the event will be published to a topic instead. All queues subscribed to the topic will receive the event. This means both of your queues will receive events from all participants.

1. Switch back to the Broker Instance and open the **"Try me tool"**.  If your Broker is not connected, plese repeat the steps 14-19 of exercise 1.4 [Exercise 1.4 - Send an event from the Try Me! Tool to your Topic](../ex1#exercise-14---send-an-event-from-the-try-me-tool-to-your-topic)

![Pic](./images/ex3-6-2.png)

2. Change to publish to a **"Topic"** and provide **aif/businesspartner/change** as value.
3. For the message content change the **"BusinessPartner"** value UserXXX to your User ID, e.g. **"User000"**. Press "**Publish**""
```json
{
	"specversion": "1.0",
	"type": "aif.businesspartner.change",
	"source": "S4H/100",
	"datacontenttype": "application/json",
	"id": "iopoR}Qa7k{IeB7xyLljsm",
	"time": "2024-07-23T15:09:31Z",
	"data": {
		"BusinessPartner": "UserXXX",
		"LastName": "John",
		"FirstName": "Doe",
		"Country": "DE",
		"City": "Walldorf",
		"PostCode": "69190",
		"Street": "Dietmar-Hopp-Allee",
		"HouseNumber": "16"
	}
}
```
![Pic](./images/ex3-7.png)

4. You should see your entry in the application. Be aware that also the message from other participants will show in the table.
![Pic](./images/ex3-8.png)

**Congratulations, you completed all exercises!**

