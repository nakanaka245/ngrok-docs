<!-- Code generated for API Clients. DO NOT EDIT. -->

#### Example Response

```json
{
	"next_page_uri": null,
	"tls_edges": [
		{
			"backend": null,
			"created_at": "2024-11-15T14:24:06Z",
			"description": "acme tls edge",
			"hostports": ["example.com:443"],
			"id": "edgtls_2otEoYHHslgA3BisI6fF09uTcN3",
			"ip_restriction": null,
			"metadata": "{\"environment\": \"staging\"}",
			"mutual_tls": null,
			"policy": null,
			"tls_termination": null,
			"traffic_policy": null,
			"uri": "https://api.ngrok.com/edges/tls/edgtls_2otEoYHHslgA3BisI6fF09uTcN3"
		},
		{
			"backend": {
				"backend": {
					"id": "bkdhr_2otEmyOKcyRZc2vSWwae3UBEcDK",
					"uri": "https://api.ngrok.com/backends/http_response/bkdhr_2otEmyOKcyRZc2vSWwae3UBEcDK"
				},
				"enabled": true
			},
			"created_at": "2024-11-15T14:23:54Z",
			"description": "acme tls edge",
			"hostports": ["endpoint-example2.com:443"],
			"id": "edgtls_2otEmzb5QdYNBDhFjkoPqytJuof",
			"ip_restriction": null,
			"mutual_tls": null,
			"policy": null,
			"tls_termination": null,
			"traffic_policy": null,
			"uri": "https://api.ngrok.com/edges/tls/edgtls_2otEmzb5QdYNBDhFjkoPqytJuof"
		}
	],
	"uri": "https://api.ngrok.com/edges/tls"
}
```
