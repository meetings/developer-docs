
# Suggested meeting resources

## Resource representation

    {
        "id": s,
        "location": s,
        "time_string": s,
        "skype_url": s,
        "created_epoch": i,
        "date_string": s,
        "enter_url": s,
        "created_date_string": s,
        "begin_epoch": i,
        "end_epoch": i,
        "timezone_string": s,
        "title": s,
        "source : s,
        "participants" : [ ${meeting_participants-resource}, ... ],
    }

## List

    GET /v1/users/:id/suggested_meetings

Deprecated:

    GET /v1/users/:id/meeting_suggestions


### Special hack

**Don't use this!** It ws a quick hack for the summary.

    GET /v1/users/:id/meetings_and_suggestions

## Hide

    PUT /v1/suggested_meetings/:id

    {
        disabled : 1,
    }

Deprecated:

    PUT /v1/meeting_suggestions/:id


## Insert

Call this function to specify the list of suggestions that currently have their beginning time within the specified timespan. If no timespan is specified, does not remove removed suggestions but still works.

    POST /v1/users/:id/suggested_meetings/set_for_source_batch

    {
        source_container_id : s,
        source_container_type : s,
        source_container_name : s,
        source_id_inside_container : s,
        source_name : s,
        source_is_primary : s,

        timespan_begin_epoch : i, // start of covered timespan, optional
        timespan_end_epoch : i, // end of covered timespan, optional

        suggestions : [
            {
                uid : s, // not necessary but preferred
                title : s,
                begin_epoch : i,
                end_epoch : i,
                description : s,
                location : s,
                participant_list : s, // '"Antti" <antti@meetin.gs>, "Jussi" <jussi@meetin.gs>'
                organizer : s, // '"Antti" <antti@meetin.gs>'
            },
            ...
        ]
    }


## Legacy batch import (DO NOT USE)

For making sure certain meeting suggestions exist in Meetin.gs you pass a JSON array string containing suggestion objects in the http parameter "batch":

    POST /v1/users/:id/suggested_meetings/batch_insert

    {
        batch : '[ { "begin_epoch" : i, "end_epoch" : i, "title" : s }, ... ]'
    }

The possible parameters for a suggestion are:

    {
        title : s,
        begin_epoch : i,
        end_epoch : i,
        uid : s,
        description : s,
        location : s,
        source : s,
        participant_list : s, // '"Antti" <antti@meetin.gs>, "Jussi" <jussi@meetin.gs>'
        organizer : s, // '"Antti" <antti@meetin.gs>'
    }
