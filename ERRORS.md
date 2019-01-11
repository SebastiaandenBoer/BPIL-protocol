# Protocol Errors

*This document lists all possible error codes and messages for both Control Tower implementations. Although the exact descriptions of error codes can vary between different Control Towers, all error codes always describe the same phenomenon/ failure.*

## Format of errors
All errors are returned as part of the ```output``` object, and are represented as follows:

```
<output>
    <errorCode>1001</errorCode>
    <errorText>
        <![CDATA[You do not have permission to manage this truck.]]>
    </errorText>
</output>
```


## Application wide errors codes (1001 - 1099)
**1001**: Invalid key. | You do not have permission to manage this truck.

**1002**: Invalid truckID. | No truck exists for this truckID.

**1003**: Geolocation does not exist. | Invalid location parameters.

**1004**: Internal SPARQL query failed.


## Error codes for AssignTruckRoute (1101 - 1199)
**1101**: The truck is already en-route to its destination. Another destination could not be set.

**1102**: Unable to calculate route.


## Error codes for RequestTruckLocation (1201 - 1299)
**N/A**


## Error codes for EstimateLoadingTime (1301 - 1399)
**1301**: List of goods cannot be empty.

**1302**: Calculated time exceeds maximum time constraints.

**1303**: Goods exceed maximum weight of 27.500kg.

**1304**: Goods exceed maximum volume of 87.43m3.


## Error codes for EstimateStagingTime (1401 - 1499)
**1401**: List of goods cannot be empty.

**1402**: Calculated time exceeds maximum time constraints.

**1403**: Goods exceed maximum weight of 27.500kg.

**1404**: Goods exceed maximum volume of 87.43m3.

## Error codes for RegisterTransportCompany (1501 - 1599)
**1501**: Cannot register more than 25 trucks.

**1502**: Name cannot be empty.
