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

## Insert

Adds new suggestion source for a given user.

    POST /v1/users/:id/suggestion_sources
    
    {
        container_type: s,
        container_id: s, // Device uuid
        name: s,
        uuid: s // FOR LEGACY REASONS the uuid must be in the form of [container_type_here]:therealcalendaruuid
    }
