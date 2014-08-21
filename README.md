# Meetin.gs developer documentation

Meetin.gs contains several API's. There also some guides on how to build well behaving application connectors. 

## [Meetin.gs Data API](https://github.com/Meetings/developer-docs/tree/master/data-api)

This API can be used to fetch and manipulate Meetin.gs data. This API can be used to build client aplications to access meeting data, automate meeting manipulation as a partner and privide information about connected applications as an application provider.

This is a HTTPS REST API which responds with JSON structures. You can authenticate to this API either as a regular user, as a Meetin.gs partner or as a Meetin.gs application provider.

https://github.com/Meetings/developer-docs/tree/master/data-api

## [Meetin.gs Affiliate Installation](https://github.com/Meetings/developer-docs/tree/master/affiliate-installation)

How to use the Meetin.gs Platform API to add Schedule -buttons to any web page.

https://github.com/Meetings/developer-docs/tree/master/affiliate-installation

## [Meetin.gs URL Scheme Parameters](https://github.com/Meetings/developer-docs/tree/master/url-scheme-parameters)

This is a documentation of the parameters our mobile applications url schemes and mobile web frontends accept in order to instruct them to start in a specific state.

https://github.com/Meetings/developer-docs/tree/master/url-scheme-parameters

## [Meetin.gs Notification API](https://github.com/Meetings/developer-docs/tree/master/notification-api) (NOT READY)

This API allows you to be notified when something matching certain criteria happens inside Meetin.gs. This API can be used to provide real time updates to clients or automate meeting manipulation in response to user actions as a partner.

This API uses a JSON structure based subscription system over HTTPS and notifications can be delivered over websockets, long polling and HTTPS callbacks. You can authenticate to this API either as a regular user or as a Meetin.gs partner.

https://github.com/Meetings/developer-docs/tree/master/notification-api

## [Meetin.gs Application connector development guidelines](https://github.com/Meetings/developer-docs/tree/master/application-guides) (NOT READY)

This section describes what you need to take into account when developing an application connector.

https://github.com/Meetings/developer-docs/tree/master/application-guides

# Local building instructions

This is mainly for markdown compilation testing purposes. Normally you would browse these through Github.

    npm install -g markdown
    ./Build.sh
    open build/index.html

