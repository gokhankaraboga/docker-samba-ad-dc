# Docker container demonstrating Samba's Active Directory Domain Controller (AD DC) support

## Run Container with Persistent(Existing) Samba Data

1. Create a file named ```.env``` containing your environment variables. env.example file can be used as example.

2. Build docker image
``` docker build -t samba-ad-dc . ```

3. Run container with 

    ```
    docker run -p 389:389 -p 636:636 -v ${DATA_PATH}/conf:/conf -v ${DATA_PATH}/krb5kdc:/etc/krb5kdc  -v ${DATA_PATH}/samba:/var/lib/samba  -e LDAP_ALLOW_INSECURE=true  -e SAMBA_DOMAIN=${SAMBA_DOMAIN}  -e SAMBA_REALM=${SAMBA_REALM} -e SAMBA_ADMIN_PASSWORD=${SAMBA_ADMIN_PASSWORD} samba-ad-dc
    ```
    
    or
    
    ``` docker-compose up ```

4. Alternatively, you can build & run at single step.
    ```
    docker-compose up --build
    ```

