---
id: script-dns

title: SCRIPT DNS
---

# SCRIPT DNS Record Type

SCRIPT records contain a JavaScript function that’s executed on each DNS query to determine the corresponding answer.

Let’s say you’re in need of a tasty dessert but don’t want to leave your command line:

```bash
~ $ dig +short TXT dessert.script.packetframe.com @script-ns.packetframe.com
"Salted Caramel Cake with Whipped Cream"
```

Under the hood, this is just a simple asynchronous JavaScript function that calls out to an API to retreive random
desserts.

```js
async function handleQuery(query) {
    return await fetch("https://random-data-api.com/api/dessert/random_dessert")
        .then(resp => resp.json())
        .then(data => {
            return {
                "authoritative": true,
                "rrs": [
                    {
                        name: query.name,
                        ttl: 300,
                        type: "TXT",
                        value: '"' + data["flavor"] + " " + data["variety"] + " with " + data["topping"] + '"'
                    }
                ]
            }
        })
}
```


More practically speaking, SCRIPT records simplify popular GeoIP DNS routing and open up a whole new range of new
DNS-based load balancing, DDoS mitigation, and traffic engineering possibilities.

We pass a query object to handleQuery and await the promise. Here’s a quick example of what that query object currently
contains:

```bash
~ $ dig +short +subnet=192.0.2.0/24 TXT query.script.packetframe.com @script-ns.packetframe.com
"{'name':'query.script.packetframe.com.','type':'TXT','subnet':'192.0.2.0/24/0','cookie':'d551f2af83ce9fda'}"
```

```js
async function handleQuery(query) {
    return {
        "authoritative": true,
        "rrs": [
            {
                name: query.name,
                ttl: 86400,
                type: "TXT",
                value: JSON.stringify(query).replaceAll('"', "'")
            }
        ]
    }
}
```
