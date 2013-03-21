# User resources

The special id "me" points to the current authorized user.

## Resource representation

### Common values

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

### Additional values for self

    {
        facebook_user_id : s,
        alternative_emails : [], (todo)
    }

## Fetch

### By id (partial)

This is currently implemented only for the requesting user.

    GET /v1/users/:id

### By meet me fragment (todo)

    GET /v1/users/

    matchmaker_fragment : s

## Update (todo) 

    PUT /v1/users/:id

