
```Javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const CommsOperation = {
  participants: [
    {
      endpointType: "default",
      identity: {
        user: {
          id: "550fae72-d251-43ec-868c-373732c2704f",
          tenantId: "72f988bf-86f1-41af-91ab-2d7cd011db47",
          displayName: "Heidi Steen"
        }
      },
      languageId: "languageId-value",
      region: "region-value",
      replacesCallId: "replacesCallId-value"
    }
  ],
  clientContext: "clientContext-value"
};

let res = await client.api('/app/calls/{id}/participants/invite')
	.version('beta')
	.post(CommsOperation);

```