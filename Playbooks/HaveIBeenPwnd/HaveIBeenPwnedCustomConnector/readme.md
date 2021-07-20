# HaveIBeenPwned Logic Apps Custom connector

This custom connector connects to HaveIBeenPwned service end point and gets the required information from the HaveIBeenPwned repository.

![HaveIBeenPwned](../HaveIBeenPwned.jpg)<br>

### Authentication methods this connector supports

*  API Key authentication

### Prerequisites for deploying Custom Connector
1. HaveIBeenPwned service end point should be known. (e.g.  https://{haveibeenpwned.com})


## Actions supported by HaveIBeenPwned custom connector

| **Component** | **Description** |
| --------- | -------------- |
| **Get all breaches for an account** | Retrieves list of all breaches for an account|
| **Get breached site/sites Information** | Retrieves list of all breaches for all site/sites|
| **Get all data classes in the system** | Retrieves list of all records that can be compromised in a breach|
| **Get all pastes for an account** | Retrieves list of all pastes for an account|


### Deployment instructions 
1. Deploy the Custom Connector by clicking on "Deploy to Azure" button. This will lead you to the wizard for deploying an ARM Template.
2. Fill in the required parameters:
    * Custom Connector Name : Enter the Custom connector name (e.g. HaveIBeenPwned_connector)
    * Service Endpoint : Enter the HaveIBeenPwned service end point (e.g. https://{haveibeenpwned.com})

[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https://dev.azure.com/SentinelAccenture/Sentinel-Accenture%20Logic%20Apps%20connectors/_git/Sentinel-Accenture%20Logic%20Apps%20connectors?path=%2FHaveIBeenPwnedCustomConnector%2Fazuredeploy&version=GBHaveIBeenPwned) [![Deploy to Azure](https://aka.ms/deploytoazuregovbutton)](https://login.microsoftonline.us/organizations/oauth2/v2.0/authorize?client_id=c836cbdb-7a5b-44cc-a54f-564b4b486fc6&response_type=code%20id_token&scope=https%3A%2F%2Fmanagement.core.usgovcloudapi.net%2F%2Fuser_impersonation%20openid%20email%20profile&state=OpenIdConnect.AuthenticationProperties%3DaURMJdv8OOjkos8hJrPp2UR3SiCuzPqKSCojZXlvmudMu2wCQivYUBL-PUpm2VklFejdDnBr9Us32MzfuH8tith-XldC_OIlCqCjwB950H9ELHA76IfBBh19cTzh9-nsHhkQkk8wQDSE6bot7rUuEQB8IDVJgDMCfv1HYuUg9brFyPen2T4DF7f3SxN7Wwxfj87B5iDMqyoU1AHKentIKfwHsDQCVmhbtWdvSgPbWWABKGY-a7b1vkmjWNmo8x5v&response_mode=form_post&nonce=637443070124899368.YjM5MDcwYzMtODJkZC00MzRmLTgxNDctMjhhZjY0MWRmNjcxZGRiOWNmMmItMDAyNS00MTIxLWE4MDUtMjdiOTE4MWJhMjg0&redirect_uri=https%3A%2F%2Fportal.azure.us%2Fsignin%2Findex%2F&site_id=501430&msafed=0&client-request-id=5cc07576-a6f1-4a94-b26f-830ed1c4ad77&x-client-SKU=ID_NET45&x-client-ver=5.3.0.0)

## Usage Examples
* Get all breaches for an account.
* Get all breached sites in the system.



