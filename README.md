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

## DB Schema 
```SQL
CREATE TABLE public.ports
(lo_code varchar(5) NOT NULL,
country_code varchar(2) NOT NULL,
port_name varchar(100) NOT NULL,
port_name_wo_diacritics varchar(100) NOT NULL,
subdivision varchar(20),
status varchar(2),
date_reviewd date,
coord_long float8,
coord_lat float8,
PRIMARY KEY (lo_code));

CREATE UNIQUE INDEX unique_query
on public.ports (lo_code);

CREATE INDEX cities
ON public.ports (port_name_wo_diacritics, port_name);

CREATE TABLE public.ports_function
("id" int4 NOT NULL,
f_id varchar(5) NOT NULL REFERENCES public.ports (lo_code),
port_function int2,
PRIMARY KEY ("id")
)

CREATE INDEX functions
ON public.ports_function (port_function);
```
## Focus
* Performance: 200ms
* Uptime: Default
* Availability: Normal
* Data consistency: Low


