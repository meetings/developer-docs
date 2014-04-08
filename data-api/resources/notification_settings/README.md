# User notification settings

## Resource representation

    {
        header: s*
        type : "push" | "email",
        id : s*,
        title: s*,
        value: 1 | 0
    }

## List

    GET /v1/users/:uid/notification_settings

## Update

    PUT /v1/users/:uid/notification_settings/:id

    {
        value: 1 | 0
    }


Returns the notification_setting object