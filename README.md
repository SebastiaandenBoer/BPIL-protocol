# BPIL Protocol 2018/2019

This repository contains a standard communications protocol for use during the Business Process Integration Lab course at the University of Twente. Intended consumers of the protocol (in the context of the case) are the various Transport Companies (TCs) and Control Towers (CTs).


# Protocol
This protocol lists the methods supported by both Control Tower groups, including the expected input and generated output. Please refer to [WebService.wsdl](WebService.wsdl) for a WSDL implementation of all methods exposed by both Control Towers.

All communication to both Control Towers mandates the use of **XML-Schema** (default for Mendix). Please refer to the [Mendix documentation of XML-Schema](https://docs.mendix.com/refguide/xml-schemas) based communication for more information.

## Notes on ```EstimateLoadingTime``` and ```EstimateStagingTime```
The unit for the parameters height, width, length is decimeter, whereas weight is expected in kilograms. Maximum volume of each list of 
goods is 87.43m3 and maximum weight is 27.500kg.

## Transport Company expectations
At some point in the business flow, the Transport Company is notified of a truck's arrival by the Control Tower. For this, the Transport Company needs to register a callback URL at the Control Tower. This happens during the initial registration of a Transport Company (```RegisterTransportCompany```). This endpoint needs to point to the ```NotifyArrival``` method **implemented through a REST service**.

**It is imperative that each Transport Company implements the ```NotifyArrival``` method and registers the corresponding endpoint during Transport Company registration.**

Once a truck has reached its destination, the URL endpoint exposing the ```NotifyArrival``` method will be called in combination with query parameters.

Transport Companies exposing the endpoint can expect incoming requests to adhere to the following format:
```
{endpoint}?TimeOfArrival={DateTime}&TripID={UUID}
```

For example, an incoming request might look like this:
```
https://www.example.com/rest/notifyArrival?TimeOfArrival=2019-01-01T09:12:01&TripID=35678ec6-83bc-499e-b1aa-295a8cba9330
```


# UUIDs
Throughout the service, UUIDs are used to identify objects.
Other actors in the business process are encouraged to use this form of identification in their own web services as well. For more information on generating UUIDs in Mendix, please visit [this page](https://forum.mendixcloud.com/link/questions/87680).


# Errors
Both Control Towers return the same error codes in cases of constraint violations. Please refer to [Errors.md](ERRORS.md) for descriptions of these errors and their formatting.
