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

### Legacy version which operates with meeting\_id & user\_id

    PUT /v1/meetings/:id/participants/:pid

## Insert (todo)

    POST /v1/meeting_participants/
  
