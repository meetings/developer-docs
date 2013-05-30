# Meetin.gs Data API

## REST Resources

* [Users](resources/users)
* [Meetings](resources/meetings)
* [Meeting participants](resources/meeting_participants)
* [Meeting time proposals](resources/meeting_time_proposals)
* [Meeting materials](resources/meeting_materials)
* [Meeting material comments](resources/meeting_material_comments)
* [Meeting material edits](resources/meeting_material_edits)
* [Highlighted meetings](resources/highlighted_meetings)
* [Suggested meetings](resources/suggested_meetings)
* [Matchmakers](resources/matchmakers)
* [Matchmaker options](resources/matchmaker_options)
* [Matchmaker locks](resources/matchmaker_locks)
* [Suggestion sources](resources/suggestion_sources)

## Action endpoints

* [Logging in](actions/login)
* [Uploading files](actions/uploads)
* [Checking heartbeats](actions/heartbeat)
* [Tracking users](actions/track)

## General principles
HTTPS REST + HTTPS action calls.
### Authentication
Authenticate using simple tokens or later with OAuth2.

Tokens needed are "user_id" and "dic", which can be sent either in request headers or as post/query params.

### Environments

For testing use:

https://api-dev.meetin.gs/

For production use:

https://api.meetin.gs/

## Return value principles

### Resource endpoints

Resource endpoints return either a json object containg the resource or a json list of the resource objects.

### Other endpoints

Other endpoints return one of keys "result" and "error".

Example of a succesfull non-resource endpoint response:

    {
        result : 1,
    }

Example of an unsuccesfull non-resource endpoint response:

    {
        error : {
            code : '400',
            message : 'Unauthorized',
        },
    }

# TODO

## Next on the todo list

    FOR MEET MET
    /users/ID/matchmakers GET
    /users/ID/matchmakers PUSH
    /matchmakers/ID/ PUT
    /matchmakers/ID/ DELETE
    /matchmakers/ GET

    FOR AB BROWSING
    /users/ID/contacts GET

    FOR AB FILLING
    /users/ID/contacts PUSH
    /contacts/ID PUT

    FOR ADDING AND DRAFT READY
    /users/ID/meetings POST
    /meetings/ID PUT (complete)
    /meetings/ID/participants POST
    /meetings/ID/draft_participants POST
    /meetings/ID/draft_participants GET
    /draft_participants/ID PUT


## Future planned API calls

    /meetings/ID DELETE
    /participants/ID DELETE
    /draft_participants/ID DELETE
    /materials/ID PUT
    /materials/ID DELETE
    /comments/ID PUT
    /comments/ID DELETE

    /meetings/ID/materials/ID/notifications GET (?)
    /meetings/ID/notifications GET (?)

    /users POST
    /users/ID GET PUT
    /users/ID/meetings GET ?created
    /users/ID/meetings POST
    /users/ID/notifications GET
    /users/ID/applications POST 
    /users/ID/applications GET (?controlled ?used)
    /users/ID/applications/ID PUT
    /users/ID/applications/ID DELETE
    /users/ID/partners POST
    /users/ID/partners GET (?controlled ?usable ?authorized)
    /users/ID/partners/ID PUT
    /users/ID/partners/ID DELETE
    /users/ID/services POST
    /users/ID/services GET
    /users/ID/services/ID PUT
    /users/ID/services/ID DELETE
    /users/ID/emails POST
    /users/ID/emails GET
    /users/ID/emails/ID PUT
    /users/ID/emails/ID DELETE

    /sessions POST
    /sessions/ID GET

    /partners POST
    /partners/ID/meetings POST GET PUT DELETE

    /matchmaking_events POST
    /matchmaking_events/ID GET PUT DELETE
    /matchmaking_events/ID/matchmakers POST GET
    /matchmaking_events/ID/locations POST GET

    /applications POST GET
    /applications/ID POST GET PUT DELETE
    /applications/ID/materials/ID POST GET PUT
    /applications/ID/materials/ID/notifications POST GET


