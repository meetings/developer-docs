# Uploading files

Normally you upload a file to the server, receive an upload\_id in the return value and then pass that upload\_id to some other endpoint to store the file association.

## Upload

    POST /v1/uploads

Is expected to receive just a normal multipart encoded POST request with a single attachment.

### Return

    {
        result : {
            upload_id : s,
        }
    }

