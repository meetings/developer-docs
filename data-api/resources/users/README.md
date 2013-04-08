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
        tos_accepted : 1|0,
        login_allowed_for_partners : [
            { id : s, name : s }, ..
        ],
        facebook_user_id : s,
        alternative_emails : [], (todo)
    }

## Fetch

### By id (partial)

This is currently implemented only for the requesting user.

    GET /v1/users/:id/

    {
        image_size : i || 50,
    }

### By meet me fragment

    GET /v1/users/

    {
        user_fragment : s,
        image_size : i || 50,
    }

## Update (todo) 

    PUT /v1/users/:id/

