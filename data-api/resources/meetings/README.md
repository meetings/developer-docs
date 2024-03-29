
# Meeting resources

## Resource representation

### Mutable values in a resource

    {
        "location_value": s, // freeform|"Online"|""
        "title_value": s, // freeform|""
        "online_conferencing_option" : s, // "skype"|""
        "skype_account" : s, // raw account name
        "begin_date" : s, // yyyy-mm-dd - uses timezone stored for user object
        "begin_time : s, // hh:mm (24h) - uses timezone stored for user object
        "begin_epoch": i, // takes preference over string versions if defined when updating and creating
        "end_date" : s, // yyyy-mm-dd - uses timezone stored for user object
        "end_time" : s, // hh:mm (24h) - uses timezone stored for user object
        "end_epoch": i,  // takes preference over string versions if defined when updating and creating
        "matchmaking_accepted": 0|1, // Can not be set to 0 if set to 1
    }

### Immmutable values in all resource responses

    {
        "id": s,
        "is_draft" : 0|1,
        "title": s, // transitionally title_string, in the future title_value, do not use this yet
        "title_string": s,
        "location": s, // transitionally location_string, in the future location_value, do not use this yet
        "location_string": s,
        "date_string": s,
        "time_string": s,
        "skype_url": s,
        "enter_url": s,
        "created_epoch": i,
        "created_date_string": s,
        "created_from_matchmaker_id" : s,
        "matchmaking_requester_name" : s,
        "matchmaking_requester_company" : s,
        "matchmaking_requester_comment" : s,
        "matchmaking_event_name" : s,
        "timezone_string": s,
        "responded_participants_count" : i,

        "participants" : [ ${participants-resource}, ... ],
        "proposals" : [ ${time_proposals-resource}, ... ],
    }

### Additional immutable values in single fetch resource responses

    {
        materials : [ ${materials-resource}, ... ],
        suggested_agenda : s,
        invite_greetings : { // this is for legacy apps and should not be used in new ones, use ones above when sending the invite
            subject : s,
            content : s,
            subject_rsvp : s,
            content_rsvp : s,
        },
    }

## Fetch

    GET /v1/meetings/:id

## List

    GET /v1/users/:id/meetings

    {
        user_id : resolve_param_user_id( req ),
        limit : req.query.limit || 10, // i
        offset : req.query.offset || 0, // i
        start_min : req.query.start_min || '', // epoch
        start_max : req.query.start_max || '', // epoch
        sort : req.query.sort || 'desc', // a|asc|ascending|d|desc|descending
        include_draft : req.query.include_draft || 0 // 1|0
    }

    GET /v1/users/:id/unscheduled_meetings (should me merged to the previous with a param)


### Special hack

**Don't use this!** It ws a quick hack for the summary.

    GET /v1/users/:id/meetings_and_suggestions

## Update

    PUT /v1/meetings/:id

In addition to normal function, also can choose a proposal by passing in the parameter:

    chosen_proposal_id

However this functionality will go away at some point and will be replaced with an action in the proposal resource

## Insert

    POST /v1/meetings

The insert request can contain the following additional parameters:

    initial_agenda : s, // html of the initial agenda
    participants : [
        { ... }, // object containing the same parameters as normal participant adding
        ...
    ]

Instead of the normal function, you can pass in the id for a meeting_suggestion object to activate:

    from_suggestion_id

If you do this, no further parameters are used and the meeting is created from the data found in this suggestion.

## Remove

    DELETE /v1/meetings/:id

## Actions

### Decline proposed meeting and send reason to users

    POST /v1/meetings/:id/matchmaking_decline

Additional parameter for telling a reason:

    decline_message

### Confriming a draft meeting

Confirming a draft meeting is done by sending invites to draft participants

    POST /v1/meetings/:id/send_draft_participant_invites

    {
        agenda : s, // can be used to set but not clear agenda
        title : s, // can be used to set but not clear title
        greeting_subject : s, // deprecated
        greeting_message : s, // deprecated
        require_rsvp : 1|0,
    }
