
# Highlighted meeting resources

## Resource representation

    {
        "location": s,
        "time_string": s,
        "created_epoch": s,
        "enter_url": s,
        "date_string": s,
        "created_date_string": s,
        "begin_epoch": i,
        "end_epoch": i,
        "timezone_string": s,
        "id": s,
        "title": s,
        "highlight": {
            "type": s,
            "message": s,
        }
    }

## List

    GET /v1/users/:id/highlighted_meetings

Deprecated:

    GET /v1/users/:id/highlights
