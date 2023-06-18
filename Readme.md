 To Create Own Registry  first setup basic authentication

## Simple Way To Deploy
* First setup Basic Authentication File
    ```
    docker run \
    --entrypoint htpasswd \
    httpd:2 -Bbn testuser testpassword > emptyTextFile

    ```

* And Then Deploy registry Docker
    ```

    docker run -d \
    -p 5000:5000 \
    --restart=always \
    --name registry \
    -v "$(pwd)"/:/auth \
    -e "REGISTRY_AUTH=htpasswd" \
    -e "REGISTRY_AUTH_HTPASSWD_REALM=Registry Realm" \
    -e REGISTRY_AUTH_HTPASSWD_PATH=/auth/htpasswd \
    -v /mnt/registry:/var/lib/registry \
    registry:2

    ```


## Or user our simple docker compose file

