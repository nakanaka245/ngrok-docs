<!-- Code generated for API Clients. DO NOT EDIT. -->

#### Example Response

```json
{
	"endpoints": [
		{
			"bindings": ["public"],
			"created_at": "2024-11-15T14:23:57Z",
			"hostport": "ad05754c2534.ngrok.paid:443",
			"id": "ep_2otEnMAGnzsjYtXKwoulZIQHERy",
			"name": "command_line",
			"principal": {
				"id": "usr_2otEkq4iaYvdfRlFMVvtQ1zWG4v",
				"uri": ""
			},
			"proto": "https",
			"public_url": "https://ad05754c2534.ngrok.paid",
			"tunnel": {
				"id": "tn_2otEnMAGnzsjYtXKwoulZIQHERy",
				"uri": "https://api.ngrok.com/tunnels/tn_2otEnMAGnzsjYtXKwoulZIQHERy"
			},
			"tunnel_session": {
				"id": "ts_2otEnRVgHcsvRfx1DBuim1DeX3a",
				"uri": "https://api.ngrok.com/tunnel_sessions/ts_2otEnRVgHcsvRfx1DBuim1DeX3a"
			},
			"type": "ephemeral",
			"updated_at": "2024-11-15T14:23:57Z",
			"upstream_url": "http://localhost:80",
			"url": "https://ad05754c2534.ngrok.paid"
		},
		{
			"bindings": ["public"],
			"created_at": "2024-11-15T14:23:55Z",
			"domain": {
				"id": "rd_2otEmxca1RDcHnZGvL8aJ1ylndD",
				"uri": "https://api.ngrok.com/reserved_domains/rd_2otEmxca1RDcHnZGvL8aJ1ylndD"
			},
			"edge": {
				"id": "edgtls_2otEmzb5QdYNBDhFjkoPqytJuof",
				"uri": "https://api.ngrok.com/edges/tls/edgtls_2otEmzb5QdYNBDhFjkoPqytJuof"
			},
			"hostport": "endpoint-example2.com:443",
			"id": "ep_2otEnBwt5uwlwuJIbHVBXoKuXbE",
			"proto": "tls",
			"public_url": "tls://endpoint-example2.com",
			"type": "edge",
			"updated_at": "2024-11-15T14:23:55Z"
		}
	],
	"next_page_uri": null,
	"uri": "https://api.ngrok.com/endpoints"
}
```
