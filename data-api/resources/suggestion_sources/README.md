# Meeting suggestion sources

## Resource representation

    {
        id => s,
        uuid => s,
        name => s,
        created_epoch => i,
        hidden_epoch => i,
        last_verify_epoch => i,
        last_activity_epoch => i,
        container_type => s, // phone | google | other
        container_id => s,
    }

## List

Returns an array of suggestion sources for a given user.

    GET /v1/users/:id/suggestion_sources

