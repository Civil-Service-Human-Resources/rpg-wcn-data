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

Once the service is running, use the following CURL commands.

Get an authentication token for the endpoint using the OAuth client key and secret:

<<<<<<< HEAD
<<<<<<< HEAD
By submiting the correct username/password as required.
=======
=======
>>>>>>> parent of 97022a5... Update README.md
~~~
curl --user rpgclient:secret \
  -X POST "http://localhost:8990/oauth/token?grant_type=password&username=wcn&password=pass
~~~

This will return an auth token:

`{"access_token":"24fb2cb7-92f0-4b10-923a-5c0e0160e0c6","token_type":"bearer","refresh_token":"9c11312c-7922-4e20-8f10-9ce0fac540a4","expires_in":1799,"scope":"read write trust"}`

Then call the data endpoint using this token:

`curl --header "Content-type: text/xml" -X POST -d "<xml><stuff></stuff><xml>" http://localhost:8990/wcnDataFeed/?access_token=24fb2cb7-92f0-4b10-923a-5c0e0160e0c6`
<<<<<<< HEAD
>>>>>>> parent of 97022a5... Update README.md
=======
>>>>>>> parent of 97022a5... Update README.md
