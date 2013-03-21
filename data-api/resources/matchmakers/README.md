# Matchmaker resources (todo)

## Resource representation

    {
        id : s,
        user_id : s,
        description : s,
    }

## Fetch

    GET /v1/matchmakers/:id

## List

### By user

    GET /v1/users/:id/matchmakers

### By meet me fragment

    GET /v1/matchmakers/

    matchmaker_fragment : s

## Update

    PUT /v1/matchmakers/:id

## Insert

    POST /v1/matchmakers/
 
