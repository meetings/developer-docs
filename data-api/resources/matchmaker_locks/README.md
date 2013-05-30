# Matchmaker lock resources

## Resource representation
    {
        id : s,
        matchmaker_id : s,
        location_id : s,
        location_string : s,
        start_epoch : i,
        end_epoch : i,

        times_string : s, // using the matchmaker time zone
    }

## Create lock

    POST /v1/matchmakers/:id/locks

    {
        begin_epoch : i,
        end_epoch : i,
    }

## Cancel lock

    DELETE /v1/matchmaker_locks/:id

## Action: Confirm reservation

    POST /v1/matchmaker_locks/:id/confirm
    
    {
        description : s,
    }

