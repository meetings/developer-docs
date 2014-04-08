# User notification settings

## Resource representation

    {
        header: s*
        type : "push | email",
        id : s*,
        title: s*
        value: true | false
    }

## List

    GET /v1/users/:uid/notification_settings

## Update

    PUT /v1/users/:uid/notification_settings

Parameters:

    {
        id: s,
        value: true | false
    }


Returns the notification_setting object