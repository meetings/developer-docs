# Meeting resources 

## Resource representation

### Values in all resource responses

    {
        "id": s*,
        "location": s*, // transitionally location_string, in the future location_value
        "location_string": s*,
        "location_value": s, // transitional, will go away after location is changed to this
        "time_string": s*,
        "skype_url": s*,
        "online_conferencing_option" : s,
        "skype_account" : s,
        "created_epoch": i*,
        "date_string": s*,
        "enter_url": s*,
        "created_date_string": s*,
        "begin_epoch": i,
        "end_epoch": i,
        "timezone_string": s*,
        "title": s*, // transitionally title_string, in the future title_value
        "title_string": s*, 
        "title_value": s, // transitional, will go away after title is changed to this
    },

### Additional values in single fetch resource responses

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
  
