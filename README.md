# BPIL Protocol 2018/2019

This repository contains a standard communications protocol for use during the Business Process Integration Lab course at the University of Twente. Intended consumers of the protocol (in the context of the case) are the various Transport Companies (TCs) and Control Towers (CTs).


# Protocol
This protocol lists the methods supported by both Control Tower groups, including the expected input and generated output. Please refer to [protocol.jsonc](protocol.jsonc) for a descriptive implementation of this protocol.

All communication to both Control Towers mandates the use of **XML-Schema** (default for Mendix). Please refer to the [Mendix documentation of XML-Schema](https://docs.mendix.com/refguide/xml-schemas) based communication for more information.


## Transport Company expectations
At some point in the business flow, the Transport Company is notified of a truck's arrival by the Control Tower. For this, the Transport Company needs to register a callback URL at the Control Tower. This happens during the initial registration of a Transport Company (```registerTransportCompany```). Once a truck has reached its destination, the URL endpoint exposing the ```notifyArrival``` method will be called.

**It is imperative that each Transport Company implements the ```notifyArrival``` method and registers the corresponding endpoint during Transport Company registration.**

The following parameters will be sent upon arrival:

```
<input>
    <timeOfArrival>1543238189</timeOfArrival>
    <truckID>xxxxxxxx-xxxx-Mxxx-Nxxx-xxxxxxxxxxxx</truckID>
</input>
```


# UUIDs
Throughout the service, UUIDs are used to identify objects.
Other actors in the business process are encouraged to use this form of identification in their own web services as well. For more information on generating UUIDs in Mendix, please visit [this page](https://forum.mendixcloud.com/link/questions/87680).


# Errors
Both Control Towers return the same error codes in cases of constraint violations. Please refer to [Errors.md](ERRORS.md) for descriptions of these errors and their formatting.
