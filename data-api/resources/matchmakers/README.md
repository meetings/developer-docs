# Matchmaker resources

## Resource representation

    {
        id : s*,
        user_id : s*,
        vanity_url_path : s,
        description : s,
        location : s,
        background_theme : s,
        background_image_url : s*,
        duration : i, // minutes
        buffer : i, // minutes
        time_zone : s,
        time_zone_name : s*,

        slots : [
            { weekday : 0, begin_second : 8  *60*60, end_second : 16 *60*60 },
            { weekday : 1, begin_second : 15 *60*60, end_second : 24 *60*60 },
            { weekday : 6, begin_second : 0  *60*60, end_second : 3  *60*60 + 30*60 },
        ],
        
        source_settings : {
            enabled : {
                [suggestion_source_uid] : 1
                ....
            },
            disabled : {
                [suggestion_source_uid] : 1
                ....
            }
        },
    }

Parameters when inserting or updating

    {
        background_upload_id : s,
    }

## Fetch

### By id

    GET /v1/matchmakers/:id

### By meet me fragments

    GET /v1/matchmakers/

    {
        user_fragment : s,
        matchmaker_fragment : s,
    }

## List

### By user

    GET /v1/users/:id/matchmakers

### By meet me fragment

    GET /v1/matchmakers/

    {
        user_fragment : s,
    }

## Update

    PUT /v1/matchmakers/:id

## Insert

    POST /v1/users/:id/matchmakers
 
