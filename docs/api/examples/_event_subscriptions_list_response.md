<!-- Code generated for API Clients. DO NOT EDIT. -->

#### Example Response

```json
{
	"event_subscriptions": [
		{
			"created_at": "2024-11-15T14:24:01Z",
			"description": "ip policy creations",
			"destinations": [
				{
					"id": "ed_2otEnpnqeyU6Ve1ii4yMFvRrSrq",
					"uri": "https://api.ngrok.com/event_destinations/ed_2otEnpnqeyU6Ve1ii4yMFvRrSrq"
				}
			],
			"id": "esb_2otEnqccDyTXZ9dQZUndsnrf0IL",
			"metadata": "{\"environment\": \"staging\"}",
			"sources": [
				{
					"type": "ip_policy_created.v0",
					"uri": "https://api.ngrok.com/event_subscriptions/esb_2otEnqccDyTXZ9dQZUndsnrf0IL/sources/ip_policy_created.v0"
				}
			],
			"uri": "https://api.ngrok.com/event_subscriptions/esb_2otEnqccDyTXZ9dQZUndsnrf0IL"
		}
	],
	"next_page_uri": null,
	"uri": "https://api.ngrok.com/event_subscriptions"
}
```
