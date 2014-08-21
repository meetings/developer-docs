# Meetin.gs URL Scheme (and web app) parameters

The Meetin.gs App should respond to the following url scheme:

    meetings://

This scheme can have parameters that should tell the app to perform some action when it is started:

    meetings://?redirect_to_meeting=4533&redirect_to_material=1234:page:1235

The same parameters should also work in the mobile web app:

    https://m.meetin.gs/?user_fragment=amv&matchmaker_fragment=meet-antti-for-lunch

User and authentication parameters:

    user_id - integer : part of auth data
    dic - string : part of auth data
    ensure_user_id - integer : should log current user out if logged in user is not the same as the passed in user, is used with meet me

Direct meeting and material opening parameters, with meet me response helper:

    redirect_to_meeting - integer : ID of the meeting which should be opened if present
    redirect_to_material - string : ID of the material which should be opened if present (depends on redirect_to_meeting)
    matchmaking_response - "accept"|"decline" : should open meeting and perform meet me request response according to value (depends on redirect_to_meeting)

Meet me page opening parameters:

    user_fragment - string : should open the meet me page for this url fragment
    matchmaker_fragment - string : should open sub-meet me page of user if present (depends on user_fragment)
    open_calendar - "1" : should open the calendar of the specified meet me page directly if specified (depends on matchmaker_fragment)
    quickmeet_key - string : should be passed along to the reserved lock if present (depends on open_calendar)

Meet me request verification view parameters:

    confirmed_matchmaker_lock_id - integer : user confirmed their email for meet me request succesfully
    expired_matchmaker_lock_id - integer : user failed to confirm their email for meet me request in time

Parameters for opening a view which tells that some feature is not yet mobile compatible:

    under_construction_message - string : this is a message about a feature that is not yet mobile compatible
    under_construction_url - string : this is a link that brave users can try on their mobile phones for not yet mobile-ready features


