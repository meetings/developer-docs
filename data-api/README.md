Meetin.gs Data API
===========

HTTPS REST. Authenticate using simple tokens or later with OAuth2.

https://api.meetin.gs/v1/

/meetings.json POST
/meetings/ID.json GET PUT DELETE
/meetings/ID/participants.json POST GET
/meetings/ID/participants/ID.json GET PUT DELETE
/meetings/ID/draft\_participants.json POST GET
/meetings/ID/draft\_participants/ID.json GET PUT DELETE
/meetings/ID/date\_suggestions.json POST GET
/meetings/ID/date\_suggestions/ID.json GET PUT DELETE
/meetings/ID/notifications.json GET
/meetings/ID/materials.json POST GET
/meetings/ID/materials/ID.json GET PUT DELETE
/meetings/ID/materials/ID/notifications.json GET
/meetings/ID/materials/ID/comments.json POST GET
/meetings/ID/materials/ID/comments/ID.json GET PUT DELETE

/users.json POST
/users/ID.json GET PUT
/users/ID/meetings.json POST GET (?created)
/users/ID/contacts.json GET
/users/ID/notifications.json GET
/users/ID/applications.json POST GET DELETE (?controlled ?used)
/users/ID/partners.json POST GET DELETE (?controlled ?usable ?authorized)
/users/ID/matchmakers.json POST GET
/users/ID/matchmakers/ID.json PUT GET DELETE
/users/ID/matchmakers/ID/date\_suggestions.json POST GET
/users/ID/matchmakers/ID/date\_suggestions/ID.json PUT GET DELETE

/partners.json POST
/partners/ID/meetings.json POST GET PUT DELETE

/matchmaking\_events.json POST
/matchmaking\_events/ID.json GET PUT DELETE
/matchmaking\_events/ID/matchmakers.json POST GET

/applications.json POST GET
/applications/ID.json POST GET PUT DELETE
/applications/ID/instances/ID.json POST GET PUT
/applications/ID/instances/ID/notifications.json POST GET

/uploads.raw POST
/uploads/ID.json GET PUT
