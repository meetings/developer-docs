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
        planning_buffer : i, // seconds
        youtube_url : s,
        available_timespans : [
            {
                start : i, // epoch in seconds
                end : i // epoch in seconds
            },
            ...
        ],
        
        time_zone : s,
        time_zone_offset : i, // seconds
        time_zone_string : s,

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
        
        online_conferencing_option : s,
        online_conferencing_data : {
            // TODO: list possible params
        },
        
        matchmaking_event_id : s,
        event_data : {
            id : i,
            name : s,
            reserve_limit : i,
            force_buffer : i, // seconds
            force_time_zone : s,
            organizer_ur : http://slush.fi/,
            force_location : s,
            default_agenda: s,
            force_duration : i, // seconds
            force_online_conferencing_option : s,
            force_online_conferencing_data : {},
            force_vanity_url_path : s,
            organizer_name : s,
            force_background_image_url : s,
            locations_description : s,
            default_description : s,
            organizer_return_url : s,
            default_background_image_url : s,
            show_youtube_url : i,
            force_available_timespans : [
                {
                    end : i, // epoch in seconds
                    start : i // epoch in seconds
                },
                ...
            ]
        }
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
 
