# Let's chat

A self-hosted chat app for small teams built by [Security Compass][seccom].

Let's Chat is a persistent messaging application that runs on SAP Cloud Platform - Cloud Foundry services. It uses Node.js buildpack and MongoDB service.

## Requirements and Installation

Command line client for Cloud Foundry [cli][cli]

You can sign-up for the free SAP Cloud Platform trial here - [SAPCP][SAPCP] - Login and Click “Start Cloud Foundry Trial” on the home screen. For more information on account creation, refer this [Blog][Blog]

## Configuration

Let's Chat can be configured by YAML (manifest.yml)

## Deployment on Cloud Foundry

Clone the Project and Navigate inside the folder which has manifest file.

`git clone https://github.com/SAP/cloud-cf-lets-chat`

Check the Regions and Hosts available for Cloud foundry environment here - [API][API]

Example: 

`cf api https://api.cf.eu10.hana.ondemand.com`

`cf help `

`cf login` (Choose your org and space)

`cf marketplace` (Choose from different plans of mongodb)

`cf create-service mongodb v3.0-dev mongodb`

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

## Support

For any question/clarification, to report an issue with SAP Cloud Platform trail account and services, please create github issues.

## Coding Samples

Any software coding and/or code lines / strings ("Code") included in this documentation are only examples and are not intended to be used in a productive system environment. The Code is only intended to better explain and visualize the syntax and phrasing rules of certain coding. SAP does not warrant the correctness and completeness of the Code given herein, and SAP shall not be liable for errors or damages caused by the usage of the Code, unless damages were caused by SAP intentionally or by SAP's gross negligence.

## Important Disclaimers on Security and Legal Aspects

This document is for informational purposes only. Its content is subject to change without notice, and SAP does not warrant that it is error-free. SAP MAKES NO WARRANTIES, EXPRESS OR IMPLIED, OR OF MERCHANTABILITY, OR FITNESS FOR A PARTICULAR PURPOSE.

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
[cli]: https://github.com/cloudfoundry/cli/releases
[SAPCP]: https://account.hanatrial.ondemand.com
[API]: https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/350356d1dc314d3199dca15bd2ab9b0e.html
[Blog]: https://blogs.sap.com/2017/05/16/sap-cloud-platform-trial-now-includes-cloud-foundry/
