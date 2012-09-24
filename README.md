Meetin.gs developer documentation
===========

Meetin.gs contains several API's. There also some guides on how to build well behaving application connectors. 

Meetin.gs Data API
-----------

This API can be used to fetch and manipulate Meetin.gs data. This API can be used to build client aplications to access meeting data, automate meeting manipulation as a partner and privide information about connected applications as an application provider.

This is a HTTPS REST API which responds with JSON structures. You can authenticate to this API either as a regular user, as a Meetin.gs partner or as a Meetin.gs application provider.


Meetin.gs Notification API
-----------

This API allows you to be notified when something matching certain criteria happens inside Meetin.gs. This API can be used to provide real time updates to clients or automate meeting manipulation in response to user actions as a partner.

This API uses a JSON structure based subscription system over HTTPS and notifications can be delivered over websockets, long polling and HTTPS callbacks. You can authenticate to this API either as a regular user or as a Meetin.gs partner.


Meetin.gs Application connector development guidelines
-----------

This section describes what you need to take into account when developing an application connector.

