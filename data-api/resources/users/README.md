# User resources

## Resource representation

The special id "me" points to the current authorized user (todo)

    {
        id : s,
        name : s,
        first_name : s,
        last_name : s,
        primary_email : s*,
        phone : s,
        organization : s,
        title : s,
        image_url : s*,
        linkedin_url : s,
    }

## Fetch

### By meet me fragment (todo)

    GET /v1/users/

    matchmaker_fragment : s

### By id (todo)

    GET /v1/users/:id

## Update (todo) 

    PUT /v1/users/:id

