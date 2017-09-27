# Let's Chat on SAP Cloud Platform

[Let's Chat][Let's Chat] is a simple chat application like slack that runs on SAP Cloud Platform - Cloud Foundry services. It uses Node.js buildpack and MongoDB services from SAP Cloud Platform.

This repository demonstrates how to build and deploy Let's chat app to SAP Cloud Platform.

## What is Cloud Foundry?

Cloud Foundry is an open source cloud platform as a service (PaaS) on which developers can build, deploy, run and scale applications on public and private cloud models. 

SAP is a Founding Platinum Level Member of the Cloud Foundry Foundation, an independent not for profit Linux Foundation Collaborative Project, whose purpose is to drive global awareness and adoption of the Cloud Foundry open source project and foster a vibrant community of contributors. More Details: [Cloud Foundry in SAP Cloud Platform][CFSAP] 

## Requirements and Installation

You need to download and install Command line client for Cloud Foundry [cli][cli]. 
Please refer [Getting started][GS] with cli for more information.

You can sign-up for the [free SAP Cloud Platform trial][SAPCP] here - Login and Click “Start Cloud Foundry Trial” on the home screen. For more information on account creation, refer [tutorial on account creation][tutorial]

## Configuration

Let's Chat can be configured by YAML (manifest.yml). Although you can deploy apps without a manifest, manifests provide consistency and reproducibility. This can be useful when when you want your apps to be portable between different clouds.

Manifests are written in YAML. The manifest in this project illustrates some YAML conventions, as follows:

The manifest begins with three dashes.

The applications block begins with a heading followed by a colon.

The application name is preceded by a single dash and one space.

Subsequent lines in the block are indented two spaces to align with name.

## Deployment on Cloud Foundry

Download the Project zip file and extract it. Navigate inside the folder which has the manifest file.

To Set the API endpoint of CLI to the cloud controller of SAP trial instance, Please use the following command.

`cf api https://api.cf.eu10.hana.ondemand.com`

Check the Regions and Hosts available for Cloud foundry environment here - [API][API]

For more help in cf commands,

`cf help `

Log on to the trial instance with your SAP ID and password.

`cf login` (Choose your org and space)

Let’s create a service instance you may want to use within your application, e.g. to store data. 

To list all services managed by service brokers execute the following command:

`cf marketplace` (Choose from different plans of mongodb)

Now, let’s create a service instance of mongodb using an available service plan.

`cf create-service mongodb v3.0-dev mongodb`

Since binding of mongodb service is already configured in manifest, you can deploy the application by executing the following command in the root folder of the project where manifest file is kept.

`cf push `

## Known Issues 

The URL for your app must be unique from other apps hosted by Cloud Foundry. Use the following options with the cf CLI to help create a unique URL:

`-n` to assign a different HOST name for the app

`--random-route` to create a URL that includes the app name and random words 

(or)

please add a suffix or prefix (or change the entire name) to the host attribute within the manifest.yml file to avoid 'The host is taken' error. 

## Features and Stuff

* BYOS (bring your own server)
* Persistent messages
* Multiple rooms
* Private and password-protected rooms
* New message alerts / notifications
* Mentions (hey @you/@all)
* Image embeds / Giphy search
* Code pasting
* File uploads (Local / [Amazon S3][s3] / [Azure][azure])
* Transcripts / Chat History (with search)
* XMPP Multi-user chat (MUC)
* 1-to-1 chat between XMPP users
* Local / [Kerberos][kerberos] / [LDAP][ldap] authentication
* [Hubot Adapter][hubot]
* REST-like API
* Basic i18n support

## License

Copyright (c) 2017 SAP SE or an SAP affiliate company. All rights reserved.
Licensed under the Apache License, Version 2.0 (the "License"); you may not use this work except in compliance with the License. You may obtain a copy of the License in the LICENSE file, or at:
[http://www.apache.org/licenses/LICENSE-2.0](http://www.apache.org/licenses/LICENSE-2.0)
Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the specific language governing permissions and limitations under the License.

[license]: https://github.com/sdelements/lets-chat/blob/master/LICENSE
[ldap]: https://github.com/sdelements/lets-chat-ldap
[kerberos]: https://github.com/sdelements/lets-chat-kerberos
[s3]: https://github.com/sdelements/lets-chat-s3
[seccom]: http://securitycompass.com/
[Let's Chat]: http://sdelements.github.io/lets-chat/
[cli]: https://github.com/cloudfoundry/cli/releases
[SAPCP]: https://account.hanatrial.ondemand.com
[API]: https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/350356d1dc314d3199dca15bd2ab9b0e.html
[tutorial]: https://www.sap.com/developer/tutorials/hcp-cf-getting-started.html
[CFSAP]: https://cloudplatform.sap.com/capabilities/runtimes-containers/cloud-foundry.html 
[GS]: https://docs.cloudfoundry.org/cf-cli/getting-started.html
