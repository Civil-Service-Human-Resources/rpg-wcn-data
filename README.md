# rpg-wcn-data
# Microservice for WCN data feed.

# Usage

## Docker

The dockerised component takes 4 environment variables to configure the OAuth for endpoint.

|Variable name    | Description   |
|---                    |---            |
|RPG_WCN_DATA_CLIENT    | Oauth client user to access the OAuth endpoint    |
|RPG_WCN_DATA_SECRET    | OAuth client secret   |
|RPG_WCN_DATA_USER      | User to generate auth token from endpoint              |
|RPG_WCN_DATA_PASSWORD  | User password              |

Run the service using:

`docker build -t rpg/data-feed .`

~~~
docker run -p 8990:8990 \
    -e "RPG_WCN_DATA_CLIENT=rpgclient" \
    -e "RPG_WCN_DATA_SECRET=secret" \
    -e "RPG_WCN_DATA_USER=wcn" \
    -e "RPG_WCN_DATA_PASSWORD=pass" \
    rpg/data-feed
~~~

##

## HTTP request

Once the service is running, data can be pushed to the following endpoint

https://rpg-wcn-data.dev.cshr-gov.uk/wcnDataFeed

By submiting the correct username/password as required.
