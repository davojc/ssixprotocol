# Data Types

This document defines the various data types used throughout the protocol. They are referred to from the entity documentations.

The data types are classified as:

**Simple types** define elementary data items such as numbers and text.

**Complex types** define more elaborate types building upon the simple types.

**Enumerations** define strings or numbers as a set of options for a particular type.

**Structures** define compound types comprising of a elements typed as one of the three classifications above. Each major structure, together with their accompanying extension types is defined on a separate page.

### Naming conventions

Types, while written in a clear and proper way including whitespacing in the text, are referenced in CamelCase when used as attribute types of structures, i.e. intermittent whitespaces are removed and the first letter after each whitespace is converted to uppercase.

*Simple and complex types, as well as enumerations* start with a lowercase letter, e.g. string, physicalLocation.

*Structures* start with an uppercase letter, e.g. DocumentType, EntityIdentifier.

*Embedding:* When a structure is used as a type of an attribute, then that structure's attribute must be included in the embedding structure (e.g. all attributes of an address would be embedded in an Entity). That also means that the embedded structure only exists within the embedded structure and cannot be "reused" in another structure.

*Referencing:* Should a structure be referenced by another structure, instead of having it embedded, then this documentation uses a dot "." to specify the identifying attribute within the referenced structure, e.g. Document.ID refers to a document identified by a particular unique id.  This also means that the referenced structure exists autonomously and thus can be referenced by several other structures.

### Lists

| Type Name    | Definition                                                   |
| ------------ | ------------------------------------------------------------ |
| \<type>[:n]  | a list of type with maximum n length; for strings, this defines the maximum string length |
| \<type>[n:]  | a list of type with minimum n length; for strings this is the minimum string length |
| \<type>[n:m] | a list of type with minimum length of n and maximum length of m; for strings this is the length must be between n and m |
| \<type>[]    | a list of type with no specific minimum or maximum length, including an empty array |



## Simple types

### Definition

| Type Name | Definition |
| - | - |
| string | any number of 8-bit or 16-bit characters concatenated, including an empty string |
| number | any number of digits comprising an integer value between -2,147,483,647 and 2,147,483,647 |
| integer | any number of digits comprising an integer value between 0 and 2,147,483,647 |
| float | ::= \<number> [ "." \<number> ] <br />any number of digits to represent a value, optionally followed by a decimal point and a fractional value of up to 5 digits |
| byte | a number in the range of 0..255 |
| boolean | a number of either 1 for true or 0 for false |



## Complex types

### Date

date ::= \<year> \<month> \<day>

year ::= integer[4]   ; representing a 4-digit year, e.g. 2023 

month ::= integer[2]	; the month, starting from 01=January, including leading zeroes

day ::= integer[2] 	; the day of the month, from 01 as its first day, inclidung leading zeroes

*Example*: `20230311`

### Time

time ::= \<hh>  \<mm>  \<ss> ["Z" | ["+" | "-"] \<hh> \<mm>]

hh ::= integer[2]   ; a value between 0 - 23

mm ::= integer[2]   ; a value between 0 - 59

*Example*: `080123Z` or `080123+0100`

### Timestamp

timestamp ::= \<date> "T" \<time>

*Example*: `20230311T080123+0100`

### Physical Location

A physical location either points to a single spot on the globe, or defines an area as a polygon having its vertices defined by locators

physicalLocation ::= \<locator> | \<locator>[] 

### Locator

The locator type specifies the source for a location

locator ::= "GPS" ":" \<latitude> \<longitude> | \<Address>

latitude ::= \<float> ["N" | "S"]

longitude ::= \<float> ["E" | "W"]

### Country

country ::= string[2] | \<string>	;  [ISO 3166-1 alpha-2 country code](http://en.wikipedia.org/wiki/ISO_3166-1) or a text description

## Enumerations

### Entity Type

The entity type comprises different natural, legal or other real or virtual organisms.

entityType ::= "person" | "organisation" | "thing"

### Trade Location Type

The trade location type specifies the type of each location involved in a trade

tradeLocationType ::= "origin" | "from" | "to" | "via"

### Document Party Role

This type specifies the role of a party attached to a document, or where a document is attached to

documentPartyRole ::= "author" | "beneficiary" | "agent" | "endorser"

### Hash Method

hashMethod ::= "SHA256WithECDSA" | "SHA256WithRSA"  ; **#todo: tbc!!**
