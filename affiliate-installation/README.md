# Meetin.gs affiliate documentation

Meetin.gs registered affiliates can add Meet Me -buttons on their users profiles to facilitate easy set up of meetings.

## Setup process

### 1. Get an API key

For now registration is done manually by emailing to antti@dicole.com. You should also let us know your token-to-email -endpoint url (see next step).

### 2. Create an token-to-email exhcange endpoint
We do not want you to have to expose user emails on your pages, so we advice you to create an token-to-email exchange endpoint that we will use to get user emails. The endpoint shoud work in the following way.

    GET https://yoursite.com/secret_token-to-email_url/?token=TOKEN&checksum=CHECKSUM
    -->
    HTTP 200 OK user@email.com
*How does the  checksum work? It should make it possible to ensure the request originated from meetin.gs.*

### 3. Install our script on your site
Add the following script tag with your API key on the pages you want to use the Meet Me -buttons. The script will find all Meet Me -button elements on pageload and convert them to Meet Me -buttons.

    <script id="mtn_affliate_script" data-api-key="YOUR_API_KEY" defer="defer" src="https://platform.meetin.gs/mtn_affiliate.js" type="text/javascript"></script>

If you add/change page content dynamically, you can always use the following call to intialize the new Meet Me -buttons currently on page.

    MTN.init();

### 4. Create Meet Me button markup where wanted
Adding the following markup will create a Meet Me -button pointing to the user whose email matches the token.

    <script type="MTN/app" data-token="USER_TOKEN" data-type="meetme|schedule"></script>














