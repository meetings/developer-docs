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

    {
        email : s,
        pin : s,
    }

### Return

    {
        user_id : s,
        token : s,
    }

## Verify Facebook token

    POST /v1/login

### POST params

    {
        code : s,
        redirect_uri : s,
    }

### Return

    {
        user_id : s,
        token : s,
    }


