# Meeting material resources

## Resource representation

    {
        "id" : s,
        "material_id": s, (old, now just id)
        "author_name": s,
        "time_ago": ,
        "object_type": s,
        "from_file": 1|0,
        "type_class": s,
        "created_epoch": i,
        "edited_epoch": i,
        "comment_count": i,
        "fetch_type": s,
        "title": s,

        "content": s,
        "download_url" : s,

        "attachment_mime": s,
        "attachment_filename": s,
        "readable_type": s,
    }

## Fetch

    GET /v1/meeting_materials/:id

## List

    GET /v1/meetings/:id/materials/

## Update

Shared document contents can be updated by first creating a [meeting material edit](../meeting_material_edits) and then storing it.

    PUT /v1/meeting_materials/:id

    {
        edit_id : s,
        content : s,
        old_content : s, // if lock is valid, old_content is ignored. if lock is invalid, content is saved if old_content matches current content.
    }

Material can be renamed by putting a new title.

    PUT /v1/meeting_materials/:id

    {
        title : s,
    }



## Insert

### Adding an image material from uploads

    POST /v1/meetings/:id/materials/

    {
        upload_id : s,
    }

