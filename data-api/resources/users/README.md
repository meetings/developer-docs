# User resources

The special id "me" points to the current authorized user.

## Resource representation

### Common values

    {
        id : s*,
        name : s, // first_name and last_name take precedence when updating if defined
        first_name : s,
        last_name : s,
        phone : s,
        organization : s,
        title : s,
        linkedin : s,
        skype : s,
        primary_email : s*,
        image_url : s*,
        * upload_id : s,
    }

### Additional values for self

    {
        timezone : s,
        tos_accepted : 1|0, // can only be set from false to true
        login_allowed_for_partners : [
            { id : s, name : s }, ..
        ]*,
        facebook_user_id : s*,
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

## Update (partial)

This is currently implemented only for the requesting user.

    PUT /v1/users/:id/

