
# Meeting participant resources

## Resource representation

    {
        "id" : s,
        "draft_object_id" : s,
        "participant_object_id" : s,
        "meeting_id" : s,
        "unanswered_proposal_count": i,
        "linkedin": s,
        "rsvp_string": s,
        "rsvp": s,
        "last_name": s,
        "organization_title": s,
        "email": s,
        "last_action_string": s,
        "organization": s,
        "initials": s,
        "is_creator": 0|1,
        "proposal_answers": {},
        "rsvp_required": 0|1,
        "name": s,
        "is_manager": 0|1,
        "phone": s,
        "image": s,
        "rsvp_status": s,
        "skype": s,
        "user_id": s,
        "first_name": s,
    }

## Fetch

    GET /v1/meeting_participants/:id

### Legacy version

Operates with `meeting_id` and `user_id`.

    GET /v1/meetings/:id/participants/:pid

## List

    GET /v1/meetings/:id/participants

## Update

    PUT /v1/meeting_participants/:id

    {
        "rsvp" : "yes" | "no",
        "proposal_answers" : ???
    }

### Legacy version

Operates with `meeting_id` and `user\_id`.

    PUT /v1/meetings/:id/participants/:pid

## Insert

This will result in either a draft participant or a real participant being created depending on the status of the meeting. To sent invitations out for already created draft participants, use the draft invitation sending action.

    POST /v1/meetings/:id/participants

### Parameters for adding participants to any type of meeting

Either a known user (must be in the user's address book):

    {
        user_id : s
    }

Or by an email and a name:

    {
        email : s,
        name : s?, // if name is provided, it overrides the phrase in the email
    }

### Additional parameters for adding participants to a non-draft meeting

    {
        greeting_subject : s, // deprecated
        greeting_message : s, // deprecated
        require_rsvp : 1|0,
    }

## Remove

    DELETE /v1/meeting_participants/:id

## Actions

### Sending draft participant invitations

Draft participants can be turned into real participants using an action to send their invites simultaneously. This is documented in the [meetings resource documentation](../meetings).

### Resending invitations

    POST /v1/meeting_participants/:id/resend_invitation
    
The effect of this action depends on wether the participant is a part of a running scheduling or not.
