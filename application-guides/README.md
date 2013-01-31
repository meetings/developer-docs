Meetin.gs Application connector development guidelines
===========

Develop a minimum viable material application
-----------

The least you need to do is to develop a web application which responds to two HTTPS endpoints you provide with an HTML document:

1. Create endpoint
2. Show endpoint

Both of these endpoints are expected to return HTML which will be rendered inside an iframe with white surroundings on various devices. Once you have these endpoints planned (or developed) you can go and register your application at http://dev.meetin.gs/.

### Create endpoint

Your create endpoint will receive a POST request with a parameter called "instance\_id". This POST tells you that a user has created a new material with the type of your application and in the future it will be referenced with the given ID. The next thing for you is to somehow associate this ID with a material instance from your own application.

The most basic way to do this is to log the user in, offer the user a list of recent objects in your system and allow the user to pick one. Make sure with your copy that the user understands that a link to the object will be shared with others in the meeting.

Once the object is confirmed to be shared, you have two main strategies you can choose to store the link between the instance ID and your own material. The first one is to simply use your own database to store an association with the instance ID and your own material and be done with it. However if you do not have an easy way to store such associations or do not want to be responsible for maintaining the associations you can use the "instance\_state" parameter in our database to store a verification hash that you can in the future use to verify that the association is indeed previously confirmed by you.

This happens by simply taking some unique id for your object, concatenate it with a secret of yours and apply a SHA256 algorithm for the resulting string. After this you store the the unique id and the SHA256 signature as the "instance\_state" parameter string in a way that you can parse and verify them in the future. If you wish you can also store some additional data about the association or your material representation in this state parameter but make sure that you insclude all the relevant state information also in your SHA256 signature so that it can not be forget to access unauthorized data in your service.

If you go along with the state string route, you can send the state string to our database along with the process of telling us that the creation process is completed. To do this you add an "instance\_state" parameter to the URL that was provided you in the initial POST request as the parameter "create\_completed\_url" and then forward your user to the resulting URL (maybe inside an iframe). If you store the association yourself you can just pass the user to the "create\_completed\_url" without modifications.

From the create completed URL the user is taken to view your newly selected material inside meetings. Your software should thus receive a request to the Show endpoint with the "instance\_id" and "instance\_state" parameters along with some other data.

### Show endpoint

When a user opens a material created to have the type of your application, your Show endpoint receives a GET request with the parameters "instance\_id" and "instance\_state" with some other data. Your endpoint should check that a valid connereturn an HTML representation of the object corresponding to the given ID. All the meeting participants can now see it in an iframe inside their Meetin.gs user interface.

At this point your application is ready for testing! Just make sure your application settings point to these two URLs and start creating new materials. If you want to fine tune some aspects of the display you might want to visit the next chapter at this point. But be sure to come back here for the last chapter to make sure your app is secure.

### Verify requests

Before actually publishing the application, you want to verify that the requests to your endpoints actually came from Meetin.gs.

When you receive a request to your endpoint, in addition to all the parameters it will also contain the parameters "keys" and "signature".
The "keys" will contain a comma separated list of HTTP parameters. You need to take the UTF8 value of each listed parameter in the order they are listed, join them together as a string and add your application secret at the end. Then you take a base64 encoded SHA256 digest of the resulting string and compare it to the "signature" parameter. If they match, you can be fairly sure that the request originated from someone who knows your application secret.

Here is a code example of how to do this in Perl:

    my $expected_sig = $cgi->param("signature");
    my @params = split ",", $cgi->param("keys");
    my $joined_values = join "", map { $cgi->param( $_ ) } @params;
    my $sig = Digest::SHA::sha256_base64( $joined_values . $app_secret );
    return ( $expected_sig eq $sig ) ? 1 : 0;

For added security we also provide an epoch timestamp of the signature generation time as the parameter "ts" which is also one of the validated keys. You can safely ignore requests which are not within a minute of the current time if your machine time is in sync.

Here is a code example of how to do this in Perl:

    my $diff = time - $cgi->param("ts");
    return ( $diff * $diff < 3600 ) ? 1 : 0;

If the received requests pass both of these tests, you can safely assume that the requesting person is allowed to see the content corresponding to the provided ID. Once your application is up and running securely, 

Fine tuning your presentation
-----------

### Provide a custom name for the material

The minimum viable material application creates a lot of materials with the same name (configurable in the application settings) which the users can then rename after creation. For many material types we can give the material a more appropriate name after the user has chosen the object from your system.

To achieve this you need to alter the URL where you forward the user after the material has been created. The URL you received from the "create\_completed\_url" parameter already contains at least one URL parameter (the "instance\_id") so it is safe to add the needed "instance\_name" parameter by appending it after an ampersand:

    my $original_url = $cgi->param( "create_completed_url" );
    my $custom_name = "Quarterly proceedings";
    return $original_url . "&instance_name=" . URI::Encode::uri_encode( $custom_name );

### Control the material iframe

Most materials have a visualization which is longer than the default iframe fits. This introduces a scrollbar to the iframe which you might want to eliminate. If you want to get rid of this scrollbar you need to be aware of the height of your material and signal this height to Meetin.gs so that the Meetin.gs UI can make the iframe height larger.

As part of the show endpoint parameters you will receive a value for "iframe\_resize\_url". To signal a need for a different iframe height you should create an empty iframe on your page and set the source as the "iframe\_resize\_url" with the desired pixel height encoded in the anchor of the URL using the format "#height-447".

To get a quicker response you should create this iframe beforehand without an anchor (this does nothing). Then when a resize is needed, you add the anchor to the iframe url and resize the iframe to signal of a new value. You can read a detailed description with a nice diagram of this cross domain iframe communication method here: http://ternarylabs.com/2011/03/27/secure-cross-domain-iframe-communication/

In order to offer the best experience for the users we suggest you start with a 250 pixel tall container with "overflow: hidden" to host your own content and when you detect your content overflowing, ask Meetin.gs to grow the iframe first before growing the size of your own container. (we could create a small script ourselves which would take control of a named div and make sure it does the right thing)

### Print prettily

By default we use the normal show endpoint to generate a separately printable view of your material. The CSS you attach can provide special rules for the print @media to achieve a nice looking print. Sometimes it is however hard to degrade the content nicely and for these situations you can specify a separate print endpoint in the application settings for generetaing a printer friendly HTML.

### Get delivered through all channels

Before the meeting and after the meeting we sent participants some selected materials directly to their email, phone or social media messaging system. If you believe your material should be delivered in this way to give heads up or to summarize a meeting, you need to provide a separate endpoint for presenting your content in a limited HTML structure.

This endpoint does not receive user identification and the output structure should hold only the following tags: h1, h2, h3, p, b/strong, i/em, ????


Integrate in to the platform
-----------

### Send notifications

TODO: edit notifications using the Data API. PUSH /application/ID/instance/ID/notifications 

### Show up in searches

TODO: searchable text and a search preview for the material using the Data API


Getting interactive
-----------

### Use user authentication

TODO: receive user id and user name in the parameters. This can be used to create all kinds of interactive editors or just to show who is currently looking at the same material.

### Provide an edit mode

TODO: the old school way: a different mode for editing. has a separate endpoint. app must handle locking by itself.


