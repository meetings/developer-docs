# Meetin.gs affiliate documentation
Meetin.gs registered affiliates can add Meet Me -buttons on their users profiles to facilitate easy meeting scheduling.

## Setup process

### 1. Register an application to get an API key

For now registration is done manually by emailing to antti@meetin.gs. We will create you an application that is initially set up in development mode and can return data for a couple of USER\_TOKENs provided by our test CSV file. After the development phase you can can choose from several ways to handle the USER\_TOKEN translation.

### 2. Install our script on your site
Add the following script tag with your API key on the pages you want to use the Meet Me -buttons. The script will find all Meet Me -button elements on pageload and convert them to Meet Me -buttons.

##### Tag

    <script id="mtn_affliate_script" data-api-key="YOUR_API_KEY" data-disable-unregistered="1" defer="defer" src="https://platform.meetin.gs/mtn_affiliate.js" type="text/javascript"></script>

##### Editable attributes

    data-api-key - your own api key
    data-disable-unregistered - if set, buttons are not shown for non Meetin.gs users

If you add/change page content dynamically, you can always use the following call to intialize the new Meet Me -buttons currently on page.

    MTN.init();

### 3. Add Meet Me button markup to add buttons
Adding the following markup will create a Meet Me -button pointing to the user matching USER\_TOKEN.

    <script type="MTN/app" data-token="USER_TOKEN" data-type="meetme|schedule" data-color="blue|silver|gray|dark"></script>
    
### 4. Provide a method for translating USER_TOKENs to emails
In Meetin.gs users are identified by their email, but we don not want you to place those emails to customers' client side pages. Thus we need a way for you to translate the USER\_TOKEN values you use to the actual user emails you want to query.

Currently Meetin.gs supports two main options: 1. An URL to a properly formatted CSV file and 2. A HTTP service for the translations. These approaches are detailed further in the upcoming subsections.

A method relying on symmetric encryption of the emails is on the roadmap and will be prioritized according to developer interest.

#### 4.1 Option 1: Provide a URL to a properly formatted CSV

A properly formatted CSV file must be UTF-8 encoded, must contain unique column names as the first row and must contain the column names "TOKEN" and "EMAIL" (case insensisive). Here is the CSV spec we consider appropriate: http://tools.ietf.org/html/rfc4180

The CSV file can also contain additional columns. Some of these are used to prefill the returned user data if the user is not yet a registered Meetin.gs user.

#### 4.2 Option 2: Provide a HTTP service for the translations

##### Request that Meetin.gs makes to your site

    GET https://yoursite.com/secret_token_to_email_url/?token=TOKEN&checksum=CHECKSUM

##### Response you send on success

    Status: 200 OK
    Response Body: user@email.com

##### Response you send on failure
    
    Status: 404 Not found

Currently the only security feature for your endpoint is that the endpoint URL should be secret and the requests should go over HTTPS. A further feature for verifying that the sender of the request is indeed Meetin.gs, we will offer a way to calculate a SHA1 hash composed of the USER_TOKEN and an application specific shared secret.
















