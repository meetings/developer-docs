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

### Legacy version which operates with meeting\_id & user\_id

    GET /v1/meetings/:id/participants/:pid   

## List

    GET /v1/meetings/:id/participants/

## Update

    PUT /v1/meeting_participants/:id
    
    {
        "rsvp" : "yes" | "no",
        "proposal_answers" : ???
    }

### Legacy version which operates with meeting\_id & user\_id

    PUT /v1/meetings/:id/participants/:pid

## Insert

This will result in either a draft participant or a real participant being created depending on the status of the meeting. To sent invitations out for already created draft participants, use the draft invitation sending action.

    POST /v1/meetings/:id/participants/

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
        greeting_subject : s,
        greeting_message : s,
        require_rsvp : 1|0,
    }

## Remove

    DELETE /v1/meeting_participants/:id

## Actions

### Sending invitations to draft participants in a draft meeting

    POST /v1/meetings/:id/send_draft_participant_invites/

    {
        greeting_message : s,
        greeting_message : s,
        require_rsvp : 1|0,
    }

