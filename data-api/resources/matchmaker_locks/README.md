# Matchmaker lock resources

## Resource representation
    {
        id : s,
        matchmaker_id : s,

        start_epoch : i,
        end_epoch : i,

        agenda : s,
        expected_confirmer_id : s,

        title : s,
        times_string : s, // using the matchmaker time zone
        creator_id : s,
        location_id : s, // currently can not be set, will be set automatically if need be
        location_string : s, // either from location_id location or from matchmaker
        created_meeting_id : s,
        created_meeting_gcal_url : s,
        created_meeting_calendar_url : s,
        creation_epoch : i,
        expire_epoch : i,
        cancel_epoch : i,
    }

## Create lock

    POST /v1/matchmakers/:id/locks

    {
        begin_epoch : i,
        end_epoch : i,
    }

## Cancel lock

    DELETE /v1/matchmaker_locks/:id

## Confirm lock

### For unauthorized users (sends email)

Emails the expected confirmer a link which can be used to actually confirm the reservation

    PUT /v1/matchmaker_locks/:id

    {
        agenda : s, // proposed agenda as text, can contain line changes
        expected_confirmer_id : s,
    }

### For authorized users (actually confirms)

Emails the confirmer and the matchmaking owner about next actions

    PUT /v1/matchmaker_locks/:id

    {
        agenda : s, // proposed agenda as text, can contain line changes
    }

## Get lock info

After confirmation the lock contains a lot of data that can be used to prepare for the upcoming meeting

    GET /v1/matchmaker_locks/:id

