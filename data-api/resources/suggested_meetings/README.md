# Suggested meeting resources

## Resource representation

    {
        "id": s,
        "location": s,
        "time_string": s,
        "skype_url": s,
        "created_epoch": i,
        "date_string": s,
        "enter_url": s,
        "created_date_string": s,
        "begin_epoch": i,
        "end_epoch": i,
        "timezone_string": s,
        "title": s,
        "source : s,
        "participants" : [ ${meeting_participants-resource}, ... ],
    }

## List

    GET /v1/users/:id/suggested_meetings/

    GET /v1/users/:id/meeting_suggestions/ (deprecated)


### Special hack

Don't use this :P It was a quick hack for the summary

    GET /v1/users/:id/meetings_and_suggestions/

## Hide

    PUT /v1/suggested_meetings/:id
    PUT /v1/meeting_suggestions/:id (deprecated)

    {
        disabled : 1,
    }
  
