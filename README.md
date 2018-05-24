# Design Specs - Modul Ports
| Version       | Owner         | Description   | Reviewer  | Date  | 
| -             | :-:           | -             | -         | -     |
| 0.1           | Jay           |  Imports // Exposes API for 'searchcontroller'             |           |    23.05.2018   |


## End Points

**Endpoint name**

[GET] getPorts 

**Description**

Returns JSON object - if result is found - to 'searchcontroller'

Requires parameters from search controller

**Input**
```JSON
{
    "Auth": Token,
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
  
  **Endpoint name**
  
[GET] putPorts 

**Description**

Imports data from defined datasource (https://datahub.io/core/un-locode)

**Input**

```JSON
{
    "Auth": Token,
    "TriggerImport": "True",
  }
  ```
**Output**

```JSON
{
    "Success": "True/False"
  }
  ```
  
  **Endpoint name**
  
[GET] DeletePorts 

**Description**

Deletes entries from DB Ports (1 request - 1 delete per ID)

**Input**

```JSON
{
    "Auth": Token,
    "ID": "12345678",
   
  }
  ```
**Output**

```JSON
{
    "Success": "True/False"
  }
  ```
## Technology

* Language: Python 3.6
* DB: MongoDB
* Caching: NA
* Testing Framework: ?

## DB Schema (as SQL Script - JSON Structure in case of NOSQL)
```NOSQL
use DB_Ports

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
## Focus
* Performance: 200ms
* Uptime: Default
* Availability: Normal
* Data consistency: Low
