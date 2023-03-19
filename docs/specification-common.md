# SSIX Technical Specification - Common Components

## Common Message Components

This section lists components used by trade messages as defined in the specification. These Common Components may be used across multiple areas.

### Participant

| Field Name | Req | Type | Description |
| - | - | - | - |
| ID | Y | string | This is a unique id that is unique within the context of this transaction |
| Name | Y | string | The name of the participant. |
| Identifiers | Y | Identifier[1:] | One or more identifiers on the trade network |


### Identifier

| Field Name | Req | Type | Description | 
| - | - | - | - |
| ID | Y | string | An identifier that can be used to identify a participant. |
| Protocol | Y | string | The identification protocol e.g. email/website/DLT identity etc |
| PublicKeyURL | N | string | Optional public key that is associated with this identifier. Ownership MAY be implicated by this location but steps should be taken to guarantee that ownership. |

### Data

| Field Name | Req | Type | Description |
| - | - | - | - |
| Name | Y | string | A free text field describing the data |
| Content | Y | byte[] | The content of the data |
| ContentType | Y | string | The [Media Type](https://www.iana.org/assignments/media-types/media-types.xhtml) of the content. e.g application/json, application/pdf, text/plain |
| Hash | Y | byte[64] | Hash of data |
| HashMethod | Y | hashMethod | The method used to hash the document |

