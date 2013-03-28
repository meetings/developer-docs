# Meeting resources 

## Resource representation

### Mutable values in a resource

    {
        "location_value": s, // freeform|"Online"|"" transitional, will go away after location is changed to this
        "title_value": s, // freeform|"" transitional, will go away after title is changed to this
        "online_conferencing_option" : s, // "skype"|""
        "skype_account" : s, // raw account name
        "begin_date" : s, // yyyy-mm-dd
        "begin_minute : s, // hh:mm (24h)
        "end_date" : s, //yyyy-mm-dd
        "end_minute" : s, // hh:mm (24h)
    }

### Immmutable values in all resource responses

    {
        "id": s,
        "is_draft" : 0|1,
        "title": s, // transitionally title_string, in the future title_value
        "title_string": s,
        "location": s, // transitionally location_string, in the future location_value
        "location_string": s,
        "begin_epoch": i,
        "end_epoch": i,
        "date_string": s,
        "time_string": s,
        "skype_url": s,
        "enter_url": s,
        "created_epoch": i,
        "created_date_string": s,
        "timezone_string": s,
    }

### Additional immutable values in single fetch resource responses

    {
        participants : [ ${participants-resource}, ... ],
        materials : [ ${materials-resource}, ... ],
        proposals : [ ${time_proposals-resource}, ... ], 
    }

## Fetch

    GET /v1/meetings/:id

## List

    GET /v1/users/:id/meetings/

    GET /v1/users/:id/unscheduled_meetings/ (should me merged to the previous with a param)

### Special hack

Don't use this :P It ws a quick hack for the summary

    GET /v1/users/:id/meetings_and_suggestions/

## Update

    PUT /v1/meetings/:id

In addition to normal function, also can choose a proposal by passing in the parameter:

    chosen_proposal_id

However this functionality will go away at some point and will be replaced with an action in the proposal resource

## Insert

    POST /v1/meetings/
  
