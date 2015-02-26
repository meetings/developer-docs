
# Matchmaker option resources

## Resource representation
    {
        id : s,
        matchmaker_id : i,
        start_epoch : i,
        end_epoch : i,
        start : s,
        end : s,
    }

## List

    GET /v1/matchmakers/:id/options

    {
        begin_epoch : i,
        end_epoch : i,
    }

## Preview

    POST /v1/users/:id/preview_matchmaker_options

    {
        slots : [ ... ], // format documented in the matchmaker resource
        begin_epoch : i,
        end_epoch : i,
        time_zone : s, // defaults to users time zone
    }
