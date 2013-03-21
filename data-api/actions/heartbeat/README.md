# Checking API service heartbeat

This just returns true using frontend workers so you can be sure that they are up. No authorization required.

## Check 

    GET /v1/heartbeat/

### Return

    {
        success : 1,
    }

