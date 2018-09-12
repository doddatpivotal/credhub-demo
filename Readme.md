# CredHub Service Broker for SpringBoot Demo

Use this demo to show how to leverage the Pivotal Cloud Foundry [CredHub Service Broker](https://docs.pivotal.io/credhub-service-broker/index.html)
to store secret values that you want to access from within your application.

1. Ensure you are logged into PCF and you have access to the credhub service from the marketplace

2. Build and push your app
```bash
mvn package
cf push
```

3. Create and bind the credhub service within your space. 

```bash
cf create-service credhub default my-credhub-secret -c '{"SECRET_CREDENTIAL":"yadayadadingdong"}'
cf bind-service credhub-demo my-credhub-secret
```

4. Test your app
```bash
curl https://<app_url>/secret/my-credhub-secret/SECRET_CREDENTIAL
```
You should expect the response to be `yadayadadingdong`.
