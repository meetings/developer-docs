# Meeting material edit resources

## Resource representation

    {
        "id": s,
        "content": s,
        "created_date": i,
        "renewed_date": i,
    }


## Sneak peek into ongoing edits

Returns a list that currently contains only the last active edit

    GET /v1/meeting_materials/:id/edits

## Start editing

This also creates a lock for the edit which expires in 15 minutes so the edit should be updated periodically

    POST /v1/meeting_materials/:id/edits

## Update edit content

This also updates the lock for the edit

    PUT /v1/meeting_material_edits/:id

    {
        content : s,
    }

## Save edit

    PUT /v1/meeting_materials/:id

    {
        edit_id : s,
        content : s,
        old_content : s,
    }

## Cancel editing

    DELETE /v1/meeting_material_edits/:id

## Action: Continue own interrupted edit

    POST /v1/meeting_materials/:id/continue_edit



