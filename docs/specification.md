# SSIX Technical Specification

## Common Message Components

This section lists components used by trade messages as defined in the specification. These Common Components may be used across multiple areas.

### Participant

| Field Name | Req | Type | Description | 
| - | - | - | - |
| ParticipantID | Y | string | This is a unique id that is unique within the context of this transaction |
| Name | Y | string | The name of the participant. |
| Identifiers | Y | list:Identifier | |


### Identifier

| Field Name | Req | Type | Description | 
| - | - | - | - |
| ID | Y | string | An identifier that can be used to identify a participant. |
| Protocol | Y | string | The identification protocol e.g. email/website/DLT identity etc |
| PublicKeyURL | N | string | Optional public key that is associated with this identifier. Ownership MAY be implicated by this location but steps should be taken to guarantee that ownership. |

### Location

| Field Name | Req | Type | Description | 
| - | - | - | - |
| Name | Y | string | A free text field describing the location |
| Country | Y | string | [ISO 3166-1](https://en.wikipedia.org/wiki/List_of_ISO_3166_country_codes) Alpha-2 country code |
| Country Subdivision | N | string | [ISO 3166-2](https://en.wikipedia.org/wiki/ISO_3166-2) Subdivision Code |
| Region | N | string | Any other 'regional' division not represented by ISO standard. |
| PhysicalLocation | at least one | list:GPS<br/>list:what3words<br/>coordinates<br/>address | Representation of the physical location. The expectation is for at least one of these options to be provided. |

### Data

| Field Name | Req | Type | Description | 
| - | - | - | - |
| Name | Y | string | A free text field describing the data |
| Content | Y | <n/a> | The content of the data |
| ContentType | Y | string | The [Media Type](https://www.iana.org/assignments/media-types/media-types.xhtml) of the content. e.g application/json, application/pdf, text/plain |
| Hash | Y | binary | Hash of data |
| HashMethod | Y | enum | The method used to hash the document |


## Messages

### Definitions

| Message Type | Description |
| - | - |
| InformationRequest | Request for information to associate with a trade |
| TradeProposal | Exchange information pre-trade |
| BatchProposal | Exchange information on several trades |
| Trade | Exchange information as part of the trade |
| BatchTrade | Trades consisting of more than one goods |


### TradeRequest

### Trade Proposal

### Batch Proposal

### Trade

### BatchTrade




## Location



