# Meeting suggestion sources

## Resource representation

    {
        id => s,
        uid => s, // will be generated using container_type,
                  // id_inside_container and possibly container_id
        name => s,
        id_inside_container => s,
        is_primary => i,
        container_id => s,
        container_type => s, // phone | google | other
        container_name => s,
    }

## Legacy params which are deprecated

    {
        type => s, // alias for "container_type"
        provider => s, // alias for "container_name"
        selected_by_default => s, // alias for "is_primary"
    }

## List

Returns an array of suggestion sources for a given user.

    GET /v1/users/:id/suggestion_sources

## Insert

Specifies all current calendars for a single container

    POST /v1/users/:id/suggestion_sources/set_container_batch
    
    {
        container_name: s,
        container_type: s,
        container_id: s, // Device uuid
        sources : [
            {
                name : s,
                id_inside_container : s,
            },
            ...
        ]
    }
