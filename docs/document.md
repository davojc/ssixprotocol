# Document

Documents represent any type of human or machine readable electronic or physical document.

### Document

| Field Name | Req | Type | Description |
| - | - | - | - |
| ID | Y | integer | An ID uniquely identifying the document within a trade network |
| Name | Y | string[:250] | A short document name. |
| Type | Y | DocumentType.ID | Specifies the type of a document |
| Parties | Y | DocumentParty[1:] | One or more parties this document addresses, belongs to, or otherwise references |
| Content | Y | ::= byte[] \| URI | The content of the document in either machine readable or human readable form, e.g. in JSON or PDF format;<br />or: a URI pointing to an external resource |
| IsHumanReadable | Y | boolean | True if the Content is human readable |
| Hash Code | Y | byte[64] | A hash checksum of the content |
| Signatures | N | DocumentSignature[] | Parties who have signed this document |



### Document Type

Document types are used to create classifications of documents within a trade network. They are added on an as-needed basis by its participants upon mutual agreement. Examples could be "LOI" (or "Letter of Intent"), "BOL" (or "Bill of Lading").

| Field Name | Req  | Type         | Description                                                  |
| ---------- | ---- | ------------ | ------------------------------------------------------------ |
| ID         | Y    | integer      | An ID uniquely identifying the document type within a trade network |
| Name       | Y    | string[:250] | A short and descriptive name.                                |
| Created By | Y    | Entity.ID    | reference to the entity that created this type (or otherwise stipulated or was decisively involved in its creation) |



### Document Party

| Field Name | Req  | Type              | Description                                    |
| ---------- | ---- | ----------------- | ---------------------------------------------- |
| Entity     | Y    | Entity.ID         | The ID representing the Entity                 |
| Role       | Y    | documentPartyRole | The role of the party in the referred document |



### Document Signature

| Field Name | Req  | Type       | Description                                                  |
| ---------- | ---- | ---------- | ------------------------------------------------------------ |
| Signature  | Y    | byte[64]   | The signature value                                          |
| Timestamp  | Y    | timestamp  | The date and time the signature was created                  |
| Public Key | Y    | byte[]     | The public key to verfiy the signature                       |
| Identifier | Y    | Identifier | The identifier to the party on the trade network, to verify the public key and check for potential retractions |



### Document Bundle

Document bundles link documents together, that belong to a particular trade, or set of trades, or in more general terms: should be treated as belonging to a common context. Also, a document can be referenced by several document bundles.

| Field Name | Req  | Type          | Description                                                  |
| ---------- | ---- | ------------- | ------------------------------------------------------------ |
| ID         | Y    | integer       | An ID uniquely identifying the document bundle within a trade network |
| Name       | Y    | string        | A brief description of the bundle                            |
| Documents  | Y    | Document.ID[] | References to all documents by ID that are part of the bundle |





## Example Document

```json
{
	"ID": 2983,
	"name": "Invoice",
	"type": 72,
	"parties": [
		{
			"entity": 1,
			"role": "author"			
		}
		{
			"entity": 2,
			"role": "recipient"			
		}
	],
	"content": "data:application/pdf;base64,JVBERi0xLjMKJcTl8uXrp/Og0MTGCjMgMCBvYmoKPD...",
	"isHumanReadable": 1
}
```

