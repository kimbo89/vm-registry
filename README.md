All responses will have the form

{
    "data": "Mixed type holding the content of the response",
    "message": "Description of what happened"
}
Subsequent response definitions will only detail the expected value of the data field

List all devices
Definition

GET /virtualmachines

Response

200 OK on success
[
    {
        "identifier": "chi3-pressero-haproxy",
        "location": "CHI",
        "ip_address": "192.168.0.2"
    },
    {
        "identifier": "ams-prod-services",
        "location": "AMS",
        "ip_address": "192.168.0.9"
    }
]
Registering a new virtualmachine
Definition

POST /virtualmachine

Arguments

"identifier":string a globally unique identifier for this device
"location":string the location for where the device/virtualmachine is hosted
"ip_address":string the IP address of the device's controller
If a device with the given identifier already exists, the existing device will be overwritten.

Response

201 Created on success
    {
        "identifier": "chi3-pressero-haproxy",
        "location": "CHI",
        "ip_address": "192.168.0.2"
    }
Lookup device details
GET /virtualmachine/<identifier>

Response

404 Not Found if the device does not exist
200 OK on success
    {
        "identifier": "chi3-pressero-haproxy",
        "location": "CHI",
        "ip_address": "192.168.0.2"
    }
Delete a device
Definition

DELETE /virtualmachine/<identifier>

Response

404 Not Found if the device does not exist
204 No Content on success