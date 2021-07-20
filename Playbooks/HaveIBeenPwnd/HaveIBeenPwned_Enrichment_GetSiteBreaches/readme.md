# HaveIBeenPwned GetSiteBreaches Enrichment Playbook
 ## Summary
 When a new azure sentinel incident is created, this playbook gets triggered and performs below actions:
 1. Fetches all the breach details for a list of sites/URL's.
 2. Updates all the collected information in incident.


![HaveIBeenPwned_Enrichment_GetSiteBreaches](./HaveIBeenPwned_Enrichment_GetSiteBreaches.PNG)<br>
### Prerequisites 
1. HaveIBeenPwned Custom Connector needs to be deployed prior to the deployment of this playbook under the same subscription and under the same resource group.
2. Generate an API key. [Refer this link on how to generate the API Key](https://haveibeenpwned.com/API/Key).

### Deployment instructions 
1. Deploy the playbook by clicking on "Deploy to Azure" button. This will lead you to the wizard for deploying an ARM Template.
2. Fill in the required parameters:
    * Playbook Name: Enter the playbook name here (e.g. HaveIBeenPwned_Enrichment_GetSiteBreaches)
    
### Post-Deployment instructions 
####a. Authorize connections
Once deployment is complete, you will need to authorize each connection.
1.	Click the Azure Sentinel connection resource
2.	Click edit API connection
3.	Click Authorize
4.	Sign in
5.	Click Save


####b. Configurations in Sentinel
1. In Azure Sentinel analytical rules should be configured to trigger an incident with risky URL/Sites. 
2. Configure the automation rules to trigger this playbook.

[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fdev.azure.com/SentinelAccenture/Sentinel-Accenture%20Logic%20Apps%20connectors/_git/Sentinel-Accenture%20Logic%20Apps%20connectors?path=%2FPlaybooks%2FHaveIBeenPwned_Enrichment_GetSiteBreaches%2Fazuredeploy.json&version=GBHaveIBeenPwned) [![Deploy to Azure](https://aka.ms/deploytoazuregovbutton)](https://login.microsoftonline.us/organizations/oauth2/v2.0/authorize?client_id=c836cbdb-7a5b-44cc-a54f-564b4b486fc6&response_type=code%20id_token&scope=https%3A%2F%2Fmanagement.core.usgovcloudapi.net%2F%2Fuser_impersonation%20openid%20email%20profile&state=OpenIdConnect.AuthenticationProperties%3DaURMJdv8OOjkos8hJrPp2UR3SiCuzPqKSCojZXlvmudMu2wCQivYUBL-PUpm2VklFejdDnBr9Us32MzfuH8tith-XldC_OIlCqCjwB950H9ELHA76IfBBh19cTzh9-nsHhkQkk8wQDSE6bot7rUuEQB8IDVJgDMCfv1HYuUg9brFyPen2T4DF7f3SxN7Wwxfj87B5iDMqyoU1AHKentIKfwHsDQCVmhbtWdvSgPbWWABKGY-a7b1vkmjWNmo8x5v&response_mode=form_post&nonce=637443070124899368.YjM5MDcwYzMtODJkZC00MzRmLTgxNDctMjhhZjY0MWRmNjcxZGRiOWNmMmItMDAyNS00MTIxLWE4MDUtMjdiOTE4MWJhMjg0&redirect_uri=https%3A%2F%2Fportal.azure.us%2Fsignin%2Findex%2F&site_id=501430&msafed=0&client-request-id=5cc07576-a6f1-4a94-b26f-830ed1c4ad77&x-client-SKU=ID_NET45&x-client-ver=5.3.0.0)

## Playbook steps explained

### When Azure Sentinel incident creation rule is triggered

Azure Sentinel incident is created. The playbook receives the incident as the input.

### Entities - Get URL's

Get the list of URL's as entities from the incident.

### For each-URL received from the incident

Iterates on the URL found in this incident and performs the following:

 1. Get all breaches for an URL/Site.

 2. If breaches found, create HTML table for site breach information such as name, pwned date, pwned count, else update no breaches found.

 3. Add a comment to the incident with the breach information collected which looks like below.

![comment to the incident](./HIBPIncident.PNG)

