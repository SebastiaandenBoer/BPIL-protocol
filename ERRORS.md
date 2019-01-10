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


## Error codes for assignTruckRoute (1101 - 1199)
**1101**: The truck is already en-route to its destination. Another destination could not be set.

**1102**: Unable to calculate route.


## Error codes for requestTruckLocation (1201 - 1299)
**N/A**


## Error codes for estimateLoadingTime (1301 - 1399)
**1301**: List of goods cannot be empty.


## Error codes for estimateStagingTime (1401 - 1499)
**1401**: List of goods cannot be empty.


## Error codes for registerTransportCompany (1501 - 1599)
**1501**: Cannot register more than 25 trucks.

**1502**: Name cannot be empty.