# Matchmaker quickmeet resources

## Resource representation
    {
        id : s*,
        matchmaker_id : i,
        creator_id : i*,
        created_date : i*,
        updated_date : i*,
        expires_date : i*,
        sent_date : i*,
        url_key : s*,
        email : s,
        name : s,
        phone : s,
        organization : s,
        title : s,
        fill_url : s*,
    }

## Add

    POST /v1/matchmakers/:id/quickmeets

## List

    GET /v1/matchmakers/:id/quickmeets

## Send or resend

    POST /v1/matchmakers/:id/quickmeets/:id/send


