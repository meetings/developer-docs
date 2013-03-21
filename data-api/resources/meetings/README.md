# Meeting resources 

## Resource representation

### Values in all resource responses

    {
        "id": s,
        "location": s,
        "time_string": s*,
        "skype_url": s,
        "created_epoch": i,
        "date_string": s*,
        "enter_url": s,
        "created_date_string": s*,
        "begin_epoch": i,
        "end_epoch": i,
        "timezone_string": s*,
        "title": s,
    },

    TODO: title_string, location_string

### Additional values in non-list resource responses

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

## Update (exists but weird)

Currently used only to choose a time proposal. Will be changed. Should later be used to update meeting data.

    PUT /v1/meetings/:id

## Insert (todo)

    POST /v1/meetings/
  
