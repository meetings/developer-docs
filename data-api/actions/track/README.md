# Tracking user actions

Used post both page views and actual actions.

Usually used by including https://track.meetin.gs/tracker.js and a javascript snippet.

## Track

    POST /v1/track

### POST parameters

    {
        seconds_ago : i,
        user_id : s,
        tracking_id : s,
        content : s,
        title : s,
        location : s,
        referrer : s,
        initial_referrer : s,
        user_agent : s,
        extra_params : s,
    }

### Return

    {
        success : 1
    }
