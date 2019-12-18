

# Customs Declarations Service end-to-end service guide

Version 0.9 December 2019
***

This guide explains how you can integrate your software with our APIs to submit Customs Declarations. It shows how the APIs fit into various end-to-end user journeys. It is intended to help software developers, designers, product owners or business analysts understand how your software needs to interact with HMRC systems.

## Overview
<!-- Section owner: Customs Declarations -->
Customs Declarations Service (CDS) is replacing the Customs Handling of Import and Export Freight (CHIEF) with a modern and flexible system that can handle anticipated future import and export growth.

[More information about the Customs Declaration Service (opens in a new tab)](https://assets.publishing.service.gov.uk/government/uploads/system/uploads/attachment_data/file/833111/Customs_Declaration_Service_toolkit.pdf).

What you need to do to get ready for the CDS will depend on how you currently make declarations using CHIEF.

[How to prepare for the Customs Declaration Service (opens in a new tab)](https://www.gov.uk/guidance/how-hmrc-will-introduce-the-customs-declaration-service).

For users who import or export outside of the European Union, there will be differences in the information they need to put in their declarations. This is due to changes to the UK Trade Tariff required by the Union Customs Code.

It is possible to complete and submit Customs Declarations using commercial software. To support this, we provide APIs to enable your application to:

•	Make a customs declaration

•	Receive business event notifications generated from requests submitted via the CDS APIs

Applications produced by external developers must subscribe to all of the CDS APIs that they wish to use – which enables access to the endpoints within the APIs. 
An application may subscribe to a single API or to multiple APIs.
Each subscription uniquely links a single external application to a single CDS API, and records the information associated with that unique link.

To use these APIs you must:

•	[Have an appropriate HMRC online account (opens in a new tab)](https://www.gov.uk/log-in-register-hmrc-online-services)

•	[Have an Economic Operator Registration and Identification (EORI) number](https://www.gov.uk/eori).

•	[Be registered for CDS](https://www.gov.uk/government/collections/customs-handling-of-import-and-export-freight-chief-replacement-programme)

•	[Go to developer hub to call an API](https://developer.service.hmrc.gov.uk/api-documentation/docs/api)

•	Have a working understanding of HTTP

•	[Have a working understanding of OAuth2](https://www.gov.uk/guidance/uk-trade-tariff-volume-3-customs-declaration-service-imports#user-authorisation-oauth2)

•	[Have a working knowledge of RESTful services](https://www.gov.uk/guidance/uk-trade-tariff-volume-3-customs-declaration-service-imports#api-authorisation-models)

•	Have a working knowledge of XML

Some APIs are restricted to Community System Providers (CSPs) (5 companies - large operators who own most of the major ports)
CSPs have relationship with CHIEF – inventory linking (port to HMRC).

## Notifications
CDS provides a combination of push and pull mechanisms to deliver notifications:

### Push notifications
•	The push notification mechanism sends notifications out to the trade system as those notifications become available. i.e. CDS ‘pushes’ notifications as they are generated, and the trade system needs to be constantly ready to receive them

•	Although pushed notifications remain in CDS for a short time after being delivered, there are no API endpoints that would enable a re-delivery to be requested

### Pull notifications
•	The pull notification mechanism holds available notifications for subsequent retrieval by the consuming system. i.e. The trade system ‘pulls’ notifications when it is ready to do so

•	API endpoints allow identification of those notifications and the retrieval of selected notifications

•	Pull retrieval also enables (within limits) previously read notifications to be re-read if necessary

## End-to-end user journeys
These journeys show examples of how to use the APIs.
Submitter (individual, agent or CSP) submits a Customs Declaration to CDS:

![](https://github.com/Richard-A-Wall/customs-declarations-end-to-end-service-guide/blob/master/source/documentation/submit_declaration.png)

Other use cases are described in [CDS 10 End to End Sequence Diagrams v2.5](https://github.com/Richard-A-Wall/customs-declarations-end-to-end-service-guide/blob/master/source/documentation/CDS10EndtoEndSequenceDiagramsv2.5180721BW.html)


More information about notifications:
CDS push notification destinations v01 (need link)

## Related API documentation
[Customs Declarations API](https://developer.qa.tax.service.gov.uk/api-documentation/docs/api)

This API enables your application to submit a Customs Declaration.

[Pull Notifications API](https://developer.service.hmrc.gov.uk/api-documentation/docs/api/service/api-notification-pull/1.0)

This API enables your application to “pull” business event notifications CDS has generated from requests submitted via the CDS APIs.

Other APIs related to the CDS APIs:

•	[Customs Inventory Linking Exports API](https://developer.service.hmrc.gov.uk/api-documentation/docs/api/service/customs-inventory-linking-exports/1.0)

•	[Customs Inventory Linking Imports API (CSP Only](https://docs.google.com/document/d/1KJB410mHnFSVO4njKGFD_4udj_K8Xc2bj2ZHy21sJRg/edit)

•	[Bulk Data File List (list of tariff codes)](https://developer.service.hmrc.gov.uk/api-documentation/docs/api/service/secure-data-exchange-bulk-download/1.0)

Other documentation related to CDS APIs:

•	[Inventory Tariff](https://github.com/hmrc/customs-declarations-end-to-end-service-guide/blob/master/source/documentation/Archive.zip)

•	[CDS 01 Inventory Linking Exports Service Design](https://github.com/Richard-A-Wall/customs-declarations-end-to-end-service-guide/blob/master/source/documentation/CDS%2001%20Inventory%20Linking%20Exports%20Service%20Design%20v1%206%20190702%20BW.DOCX.pdf)

•	[CDS 01 ILE Technical Completion Matrix](https://github.com/Richard-A-Wall/customs-declarations-end-to-end-service-guide/blob/master/source/documentation/CDS%2001%20ILE%20Technical%20Completion%20Matrix%20v2.1%20190430%20DF.XLSX)

•	[CDS 02 Inventory Linking Imports Service Design](https://github.com/Richard-A-Wall/customs-declarations-end-to-end-service-guide/blob/master/source/documentation/CDS%2002%20Inventory%20Linking%20Imports%20Service%20Design%20v2.2%20180706%20BW.pdf)

•	[Tariff_Data_Export.pdf](https://github.com/Richard-A-Wall/customs-declarations-end-to-end-service-guide/blob/master/source/documentation/Tariff_Data_Export.pdf)

•	[DispatchDataExport-XML-Data.xsd](https://github.com/Richard-A-Wall/customs-declarations-end-to-end-service-guide/blob/master/source/documentation/DispatchDataExport-XML-Data.xsd)

•	[ECDP-Tariff Web services documentation (Annex IV)](https://github.com/Richard-A-Wall/customs-declarations-end-to-end-service-guide/blob/master/source/documentation/Annex-IV-extraction-elements-1.8.5.pdf)

•	[Taric User Guide](https://github.com/Richard-A-Wall/customs-declarations-end-to-end-service-guide/blob/master/source/documentation/TARIC%20User%20Guide%20Revision%202.pdf)

•	[CDS – Tariff Download service -Identifying Duty Rates v1.0](https://github.com/Richard-A-Wall/customs-declarations-end-to-end-service-guide/blob/master/source/documentation/CDS%20-%20Tariff%20Download%20Service%20-Identifying%20Duty%20Rates%20v1.0.docx.pdf)

## Errors

Errors specific to each API are shown in the Endpoints section, under Response.

See our [reference guide](https://developer.service.hmrc.gov.uk/api-documentation/docs/reference-guide#errors) for more on errors.

Specific CDS backend errors: [CDS 03 Codelists and WCO References](https://github.com/hmrc/customs-declarations-end-to-end-service-guide/blob/master/source/documentation/Annex-IV-extraction-elements-1.8.5.pdf).



## Changelog
<!--- Section owner: Customs Declarations --->

### Version 0.9

December 2019

What changed:

What changed:
•	Restructuring of content following meeting with SDST (3 December 2019)

•	Links to reference material

•	Removal of duplicated information

•	Addition of extra overview information and pre-requisites

•	Addition of Notifications information from “CDS Push Notifications Destinations” John Best 7 November 2019
