# Trade

Trades represent the exchange of goods and services between entities on a trade network.

### Trade

| Field Name | Req | Type | Description |
| - | - | - | - |
| ID | Y | integer | An ID uniquely identifying the trade within a trade network |
| Parties | Y | TradeParty[1:] | The parties this trade addresses |
| Products | Y | TradeProduct[1:] | A list of products that are subject to the trade |
| Documents | Y | Document.ID | References to Documents that belong to the trade |
| Locations | Y | TradeLocation[2:] | There must be at least two locations attached to a trade, of types "from" and "to". Additional locations can be added as needed |



### Trade Party

| Field Name | Req  | Type              | Description                                    |
| ---------- | ---- | ----------------- | ---------------------------------------------- |
| Entity     | Y    | Entity.ID         | The ID representing the Entity                 |
| Role       | Y    | documentPartyRole | The role of the party in the referred document |



### Trade Product

| Field Name  | Req  | Type             | Description                        |
| ----------- | ---- | ---------------- | ---------------------------------- |
| Description | Y    | string           | A short description of the product |
| Quantity    | Y    | float            | The trade quantity                 |
| Unit        | Y    | ProductUnit.Code | The unit of the trade quantity     |



### Product Unit

Product units are used to create classifications of quantifiable units in a trade system. They are added on an as-needed basis by its participants upon mutual agreement. Examples could be "m3" (or "cubic metres"), "sqm" (or "square metres").

| Field Name  | Req  | Type        | Description                                                  |
| ----------- | ---- | ----------- | ------------------------------------------------------------ |
| Code        | Y    | string[:10] | A code assigned to the unit that must be unique within the trade system, e.g. "m3" |
| Description | Y    | string      | A brief clear text description, e.g. "cubic metres"          |



### Trade Location

| Field Name  | Req  | Type              | Description                                                  |
| ----------- | ---- | ----------------- | ------------------------------------------------------------ |
| Type        | Y    | tradeLocationType | Specifies the type of location                               |
| Location    | Y    | physicalLocation  | References a spot or area on the globe                       |
| Description | Y    | string            | a short description of the location                          |
| Quantity    | N    | float             | optionally: the total quantity of products delivered from or to the location |
