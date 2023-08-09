# Check DeBank Networks

1. Query Debank for the current list of supported chains

{% swagger method="get" path="" baseUrl="https://pro-openapi.debank.com/v1/chain/list" summary="Get the current list of supported chains from DeBank" expanded="true" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="header" name="AccessKey" required="true" %}
DeBank API Key
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
```json
{
  "id": "op",
  "community_id": 10,
  "name": "Optimism",
  "native_token_id": "op",
  "logo_url": "https://static.debank.com/image/chain/logo_url/op/01ae734fe781c9c2ae6a4cc7e9244056.png",
  "wrapped_token_id": "0x4200000000000000000000000000000000000006",
  "is_support_pre_exec": true
}
```
{% endswagger-response %}
{% endswagger %}

2. Compare it against the defined network list in the project\


{% embed url="https://github.com/tradescrow/website/blob/develop/src/data/chains.ts" %}

3. Add any missing chains, following formatting guidelines, and then add it to the \`chains\` array
