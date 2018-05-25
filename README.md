# Design Specs - Modul Ports
| Version       | Owner         | Description   | Reviewer  | Date  |  Internal Service name  | 
| -             | :-:           | -             | -         | -     | -         | 
| 0.1           | Jay           |  Imports // Exposes API for 'searchcontroller'             |           |    23.05.2018   |ports   |

## End Points

**Endpoint name**

[GET] /port 

**Description**

Returns JSON object - if result is found - to 'searchcontroller'

Requires parameters from search controller

**Input**
```JSON
{
    "CountryLocation": "AUADL",
    "Name": "Adelaide
}
  ```
  
**Output**
```JSON
{
    "Change": "",
    "CountryLocation": "AUADL",
    "Name": "Adelaide
    "NameWoDiacritics": "Adelaide",
    "Subdivision": "SA"
    "Status": "AC",
    "Function": "12345---"
    "Date": "0307",
    "IATA": ""
    "Coordinates": "34555 13835E",
    "Remarks": ""
}
  ```
________________________________________

**Endpoint name**
  
[PUT] /port 

**Description**

Imports data from defined datasource (https://datahub.io/core/un-locode)

**Input**

```JSON
{
    "TriggerImport": true,
}
  ```
**Output**

```JSON
{
    "Success": true/false,
    "ID": id
}
  ```
________________________________________

**Endpoint name**
  
[DELETE] /port 

**Description**

Softdeletes (sets validitiy field false) in DB 

**Input**

```JSON
{
    "TransactionID": int,
    "ID": "12345678"
   
}
  ```
**Output**

```JSON
{
    "Success": true/false
}
  ```
## Technology

* Language: Python 3.6
* DB: postgres
* Caching: NA
* Testing Framework: ?

## DB Schema (as SQL Script - JSON Structure in case of NOSQL)
```NOSQL
use DB_Ports

{
    "Change": string,
    "CountryLocation": string,
    "Name": string
    "NameWoDiacritics": string
    "Subdivision": string
    "Status": string
    "Function": string
    "Date": string
    "IATA": string
    "Coordinates": string
    "Remarks": string
}
```
## Focus
* Performance: 200ms
* Uptime: Default
* Availability: Normal
* Data consistency: Low


