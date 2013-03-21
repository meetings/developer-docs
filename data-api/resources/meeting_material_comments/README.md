# Meeting material comment resources

## Resource representation

    {
        "id": s,
        "is_private": s,
        "date": s,
        "content": s,
        "edited_by": s,
        "date_ago": s,
        "datetimestamp": s,
        "order": i,
        "content_stripped": s,
        "post_id": s,
        "content_plaintext": s,
        "user_image": s,
        "edited": i,
        "thread_id": s,
        "ts": i,
        "depth": i,
        "user_organization": s,
        "parent_post_id": s,
        "user_name": s,
        "last_changed": i,
        "published": i,
        "content_raw": s,
        "user_id": s,
        "date_epoch": i,
        "user_initials": s,
    }

## List

    GET /v1/meeting_materials/:id/comments/

### Previous endpoint (deprecated)

    GET /v1/materials/:id/comments/

## Update (todo)

    PUT /v1/meeting_material_comments/:id/

## Insert

    POST /v1/meeting_materials/:id/comments/

### Previous endpoint (deprecated)

    POST /v1/materials/:id/comments/
  
