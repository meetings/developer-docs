# Matchmaker lock resources

## Resource representation
    {
        id : s,
        matchmaker_id : s,
        start_epoch : i,
        end_epoch : i,
        agenda : s,

        times_string : s, // using the matchmaker time zone
        creator_id : s,
        expected_confirmer_id : s, // can be a user just created in confirm reservation 
        location_id : s, // currently can not be set, will be set automatically if need be
        location_string : s, // either from location_id location or from matchmaker
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
        agenda : s, // proposed agenda as text, can contain line changes
        expected_confirmer_id : s
    }

