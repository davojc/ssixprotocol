# Document

Documents represent any type of human or machine readable electronic or physical documents.

### Document

| Field Name | Req | Type | Description |
| - | - | - | - |
| ID | Y | integer | An ID uniquely identifying the document within a trade network |
| Name | Y | string[:250] | A short document name. |
| Type | Y | DocumentType.ID | Specifies the type of a document |
| Parties | Y | DocumentParty[1:] | The parties this document addresses, belongs to, or otherwise references |
| Content | Y | byte[] | The content of the document in either machine readable or human readable form, e.g. a JSON or PDF |
| IsHumanReadable | Y | boolean | True if the Content is human readable |

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

### Document Bundle

Document bundles link documents belonging to a particular trade or set of trades or other in more general terms: belonging to a common context.

| Field Name | Req  | Type          | Description                                                  |
| ---------- | ---- | ------------- | ------------------------------------------------------------ |
| ID         | Y    | integer       | An ID uniquely identifying the document bundle within a trade network |
| Documents  | Y    | Document.ID[] | References to all documents by ID that are part of the bundle |
