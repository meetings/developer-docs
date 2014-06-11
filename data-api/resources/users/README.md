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
        meetme_description : s,
        meetme_background_theme : 'u'|'c'|[number],
        meetme_background_image_url : s, // stored only if theme is 'u'
        * meetme_background_upload_id : s // takes effect with theme 'c'
    }

### Additional values for self

    {
        time_zone : s,
        tos_accepted : 1|0, // can only be set from false to true
        login_allowed_for_partners : [
            { id : s, name : s }, ..
        ]*,
        facebook_user_id : s*,
        alternative_emails : [], (todo)
        is_pro : 1|0,
        is_trial_pro : 1|0,
        is_free_trial_expired : 1|0,
        meetme_fragment : s,
        source_settings : {
            enabled : {
                [suggestion_source_uid] : 1,
                ...
            },
            disabled : {
                [suggestion_source_uid] : 1,
                ...
            }
        },
        available_themes : [
            'blue',
            ...
        ],
        custom_background_theme : s, // theme_name
        custom_background_image_upload_id : s,
        custom_background_image_url : s,
        custom_header_image_upload_id : s,
        custom_header_image_url : s,
        -- timezone : s, // deprecated for time_zone
        -- matchmaker_fragment : s, // deprecated over meetme_fragment
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

### By email

    GET /v1/users/

    {
        email : s,
        image_size : i || 50,
    }

    Returns data depending on the connection with the authenticated user. Always returns at least the id even when not authenticated.

## Create a non-existing user

Currently implemented only as part of the matchmaker reservation flow.

    POST /v1/users/

    Additional required params when creating:

    {
        machmaker_lock_id : s, // unique active lock required in order to create
        primary_email : s, // mandatory for now, returns error if user exists
    }

    Returns error if user already exists or an user has already been created for the lock. On success returns simply:

    {
        id : s,
    }

## Update

This is currently implemented only for the requesting user.

    PUT /v1/users/:id/

## Start free trial

Works only for self

    POST /v1/users/:id/start_free_trial

Returns

    {
        success : 1|0,
    }

## Send an email reminder

Send an email that contains a link to a page where user can buy to pro membership.

Works only for self

    POST /v1/users/:id/send_pro_features_email

Returns

    {
        success : 1|0,
    }
