# Meeting time proposal resources

## Resource representation

    {
        id => s,
        begin_epoch => i,
        end_epoch => i,
        time_string => s,
        date_string => s,
        timezone_string => s,
    }

## List

Should always be received along with meeting information.

## Insert (todo)

There is still ambiguity whether all will be posted at the same time or one by one

    POST /v1/meetings/:id/time_proposals/

## Delete (todo)

    DELETE /v1/meeting_time_proposals/:id/

## Action: Choose (todo)

    POST /v1/meeting_time_proposals/:id/choose/

### Deprecated but working choose

    POST /v1/meetings/:id/

    


