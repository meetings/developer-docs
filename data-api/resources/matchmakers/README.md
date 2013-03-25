# Matchmaker resources

## Resource representation

    {
        id : s*,
        user_id : s*,
        description : s,
        location : s,
        background_url : s*,
        duration : i, // minutes
        buffer : i, // minutes
        time_zone_id : s,
        time_zone_name : s*,

        slots : [
            { weekday : 'mon', begin_hour : "8:30", end_hour : "13" },
            { weekday : 'mon', begin_hour : "15", end_hour : "16:30" },
            { weekday : 'mon', begin_hour : "23", end_hour : "24" },
            { weekday : 'tue', begin_hour : "00", end_hour : "3:30" },
        ],
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

## Update (todo)

    PUT /v1/matchmakers/:id

## Insert (todo)

    POST /v1/matchmakers/
 
