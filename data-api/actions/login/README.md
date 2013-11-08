# How to log the user in

## Request log in email

    POST /v1/login

### POST params

    {
        email : s,
        preferred_app : ?,

        ip : s,
        allow_register : 1|0,
        return_host : s,
        tracking_id : s,
    }

## Request log in PIN code

    POST /v1/login

### POST params

    {
        email : s,
        include_pin : 1,

        ip : s,
        allow_register : 1|0,
        return_host : s,
        tracking_id : s,
    }


## Verify PIN code

    POST /v1/login

### POST params

Email is the primary way to find the user but for temp users user_id used. Send both if you know them.

    {
        user_id : s,
        email : s,
        pin : s,
    }

### Return

    {
        user_id : s,
        token : s,
        tos_accepted : 1|0,
    }

## Verify Facebook token

    POST /v1/login

### POST params

    {
        fb_code : s,
        fb_redirect_uri : s,
    }

### Return

    {
        user_id : s,
        token : s,
        tos_accepted : 1|0,
    }
    
## Verify Google token

    POST /v1/login

### POST params

    {
        google_code : s,
        google_redirect_uri : s,
    }

### Return

    {
        user_id : s,
        token : s,
        tos_accepted : 1|0,
    }

