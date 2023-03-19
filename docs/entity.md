# Entity

An entity describes a natural, legal or otherwise real or ficticious body or thing, and their relationships between each other.

### Entity

| Field Name | Req | Type | Description |
| - | - | - | - |
| EntityID | Y | integer | This is an id to uniquely identify each entity. It must be unique within one trade network. |
| Name | Y | string | The name of the entity. |
| Type | Y | entityType | The type of this entity. |
| Locations | Y | physicalLocation[1:] | The physical locations of this entity |
| Creation Date | Y | date | The date this entity was born, incorporated, invented or put in operation. |
| Legal ID | N | string | The legal identifier of the entity, e.g. a company registration number or a TIN. |
| Legal Country | N | country | The country where the entity is legally registered or was born. |
| Relationships | N | EntityID[] | Relations to other entities |

### Entity Identifier

| Field Name | Req  | Type   | Description                          |
| ---------- | ---- | ------ | ------------------------------------ |
| Name       | Y    | string | The name of the entity               |
| Legal ID   | Y    | number | An ID legally identifying the entity |



### Address

| Field Name    | Req  | Type    | Description                                                  |
| ------------- | ---- | ------- | ------------------------------------------------------------ |
| Country       | Y    | Country | [ISO 3166-1](https://en.wikipedia.org/wiki/List_of_ISO_3166_country_codes) Alpha-2 country code |
| Region        | N    | string  | [ISO 3166-2](https://en.wikipedia.org/wiki/ISO_3166-2) Subdivision Code |
| PO Box Number | N    | string  | Post office box number                                       |
| Postal Code   | Y    | string  | The postal code                                              |
| Street        | Y    | string  | The street address   |                                        |
| Locality      | N    | string  | The locality in which the street address is, and which is in the region. For example, "Regina House". |
| Email         | N    | string  | optional: an email address                                   |
| Phone         | N    | string  | optional: a telephone number                                 |
| Fax           | N    | string  | optional: a fax number                                       |

​	
