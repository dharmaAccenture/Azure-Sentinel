  # HaveIBeenPwned Logic Apps Custom Connector and playbook templates

  ![HaveIBeenPwnedCustomConnector](./HaveIBeenPwned.jpg)<br>


## Table of Contents

1. [Overview](#overview)
1. [Deploy Custom Connector + 4 Playbook templates](#deployall)
1. [Authentication](#importantnotes)
1. [Prerequisites](#prerequisites)
1. [Deployment](#deployment)
1. [Post Deployment Steps](#postdeployment)
1. [References](#references)
1. [Limitations](#limitations)


<a name="overview">

# Overview

Have I Been Pwned is a website that allows Internet users to check whether their personal data has been compromised by data breaches.

<a name="deploy">

# Deploy Custom Connector + 4 Playbook templates
This package includes:
* Custom connector for HaveIBeenPwned.
* Four playbook templates leverage HaveIBeenPwned custom connector.

You can choose to deploy the whole package : connector + all four playbook templates, or each one seperately from it's specific folder.

[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fdev.azure.com/SentinelAccenture/_git/Sentinel-Accenture%20Logic%20Apps%20connectors?version=GBPaloAlto-PAN-OS&path=%2Fazuredeploy.json) [![Deploy to Azure](https://aka.ms/deploytoazuregovbutton)](https://login.microsoftonline.us/organizations/oauth2/v2.0/authorize?client_id=c836cbdb-7a5b-44cc-a54f-564b4b486fc6&response_type=code%20id_token&scope=https%3A%2F%2Fmanagement.core.usgovcloudapi.net%2F%2Fuser_impersonation%20openid%20email%20profile&state=OpenIdConnect.AuthenticationProperties%3DaURMJdv8OOjkos8hJrPp2UR3SiCuzPqKSCojZXlvmudMu2wCQivYUBL-PUpm2VklFejdDnBr9Us32MzfuH8tith-XldC_OIlCqCjwB950H9ELHA76IfBBh19cTzh9-nsHhkQkk8wQDSE6bot7rUuEQB8IDVJgDMCfv1HYuUg9brFyPen2T4DF7f3SxN7Wwxfj87B5iDMqyoU1AHKentIKfwHsDQCVmhbtWdvSgPbWWABKGY-a7b1vkmjWNmo8x5v&response_mode=form_post&nonce=637443070124899368.YjM5MDcwYzMtODJkZC00MzRmLTgxNDctMjhhZjY0MWRmNjcxZGRiOWNmMmItMDAyNS00MTIxLWE4MDUtMjdiOTE4MWJhMjg0&redirect_uri=https%3A%2F%2Fportal.azure.us%2Fsignin%2Findex%2F&site_id=501430&msafed=0&client-request-id=5cc07576-a6f1-4a94-b26f-830ed1c4ad77&x-client-SKU=ID_NET45&x-client-ver=5.3.0.0)


# HaveIBeenPwned connector documentation 

<a name="authentication">

# Authentication
Authentication methods this connector supports- [API Key authentication](https://{haveibeenpwned.com/api/v3)

<a name="prerequisites">

# Prerequisites for using and deploying Custom Connector + 3 playbooks
1. HaveIBeenPwned service end point should be known. (e.g. https://{haveibeenpwned.com})
2. Generate an API key. [Refer this link on how to generate the API Key](https://haveibeenpwned.com/API/Key)


<a name="deployment">

# Deployment instructions 
1. Deploy the Custom Connector and playbooks by clicking on "Deploy to Azure" button. This will take you to deploying an ARM Template wizard.
2. Fill in the required parameters for deploying custom connector and playbooks

| Parameters | Description |
|----------------|--------------|
|**For Custom Connector**|
|**Custom Connector name:**| Enter the Custom connector name (e.g. contoso HaveIBeenPwned connector)|
|**Service Endpoint:** | Enter the HaveIBeenPwned service end point (e.g. https://{haveibeenpwned.com})|
|**For Playbooks**|
|**HaveIBeenPwned Enrichment GetAccountBreaches:**|  Enter the playbook name for account breaches (e.g. HaveIBeenPwned Playbook)|
|**HaveIBeenPwned Enrichment GetSiteBreaches:** | Enter the playbook name for site breaches (e.g. HaveIBeenPwned Playbook)| 
|**HaveIBeenPwned Response On Teams:** |Enter the playbook name for response on teams (e.g. HaveIBeenPwned Playbook)|
|**HaveIBeenPwned Send Email :** |Enter the playbook name for sending email (e.g. HaveIBeenPwned Playbook)|

<a name="postdeployment">

# Post-Deployment instructions 
After deploying response from Teams playbook, we need to select the Teams group and Teams channel from the dropdown in logic app designer.
## a. Authorize connections
Once deployment is complete, you will need to authorize each connection.
1.	Click the Azure Sentinel connection resource
2.	Click edit API connection
3.	Click Authorize
4.	Sign in
5.	Click Save
6.	Repeat steps for other connections such as Teams connection,Office 365 connection and HaveIBeenPwned API Connection (For authorizing the HaveIBeenPwned API connection, API Key needs to be provided)

## b. Configurations in Sentinel
1. In Azure sentinel analytical rules should be configured to trigger an incident with risky user account or site. 
2. Configure the automation rules to trigger the playbooks.


<a name="references">

#  Reference to the playbook templates and the connector

 Connector
* [HaveIBeenPwned Custom Connector](https://dev.azure.com/SentinelAccenture/_git/Sentinel-Accenture%20Logic%20Apps%20connectors?version=GBHaveIBeenPwned&path=%2FHaveIBeenPwnedCustomConnector%2Fazuredeploy.json)

Playbooks
* [HaveIBeenPwned_Enrichment_GetAccountBreaches : Playbook to GetAccountBreaches and update to incident](https://dev.azure.com/SentinelAccenture/_git/Sentinel-Accenture%20Logic%20Apps%20connectors?version=GBHaveIBeenPwned&path=%2FPlaybooks%2FHaveIBeenPwned_Enrichment_GetAccountBreaches%2Fazuredeploy.json)
* [HaveIBeenPwned_Enrichment_GetSiteBreaches : Playbook to GetSiteBreaches and update to incident](https://dev.azure.com/SentinelAccenture/_git/Sentinel-Accenture%20Logic%20Apps%20connectors?version=GBHaveIBeenPwned&path=%2FPlaybooks%2FHaveIBeenPwned_Enrichment_GetSiteBreaches%2Fazuredeploy.json)
* [HaveIBeenPwned_ResponseOnTeams : Playbook to act based on Response from Teams](https://dev.azure.com/SentinelAccenture/_git/Sentinel-Accenture%20Logic%20Apps%20connectors?version=GBHaveIBeenPwned&path=%2FPlaybooks%2FHaveIBeenPwned_ResponseonTeams%2Fazuredeploy.json)
* [HaveIBeenPwned_SendEmail : Playbook to send email automatically](https://dev.azure.com/SentinelAccenture/_git/Sentinel-Accenture%20Logic%20Apps%20connectors?version=GBHaveIBeenPwned&path=%2FPlaybooks%2FHaveIBeenPwned_SendEmail%2Fazuredeploy.json)

<a name="limitations">

# Known Issues and Limitations
* We need to authorize the connections after deploying the playbooks.



