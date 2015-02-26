
# Skeletons

## Resource representation

    {
        id : s,
    }

## Fetch

    GET /v1/skeletons/:id

## List

    [ ${skeletons-resource}, ... ]

### By user

    GET /v1/users/:id/skeletons

### By meeting

    GET /v1/meetings/:id/skeletons

### By search criteria

    GET /v1/skeletons

    skeleton_param : s

## Update

    PUT /v1/skeletons/:id

## Insert

    POST /v1/skeletons
