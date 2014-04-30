# Meeting material comment resources

## Resource representation

    {
        "id": s,
        "content": s, // this is the only writable element
        "content_plaintext": s,
        "content_stripped": s,
        "date_epoch": i,
        "user_image": s,
        "user_initials": s,
        "user_name": s,
        "user_organization": s,

        "is_private": s,
        "date": s,
        "edited_by": s,
        "date_ago": s,
        "datetimestamp": s,
        "order": i,
        "post_id": s,
        "edited": i,
        "thread_id": s,
        "ts": i,
        "depth": i,
        "parent_post_id": s,
        "last_changed": i,
        "published": i,
        "content_raw": s,
        "user_id": s,
    }

## List

    GET /v1/meeting_materials/:id/comments/
    
    {
        image_size : i, // what is the height and width of the profile images returned for commenters
    }

## Insert

    POST /v1/meeting_materials/:id/comments/

    {
        content : s,
        image_size : i,
    }

## Remove 

    DELETE /v1/meeting_materials/:materialid/comments/:id

## Update (todo)

    PUT /v1/meeting_material_comments/:id/

    {
        content : s,
        image_size : i,
    }


