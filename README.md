# wso2
Implemtation of wso2 for API micro gateway management

1. Microgateway Toolkit 3.2.0 setup

    ```bash
    ## WSO2 API Microgateway toolkit distribution ##
    wget https://github.com/wso2/product-microgateway/releases/download/v3.2.0/wso2am-micro-gw-toolkit-linux-3.2.0.zip

    ## UNZIP the ZIP file
    unzip wso2am-micro-gw-toolkit-linux-3.2.0.zip

    ## change into below directory and copy the path
    cd wso2am-micro-gw-toolkit-linux-3.2.0/bin
    pwd

    ##
    export PATH=$PATH:<paste the copied path from above command>
    ```
2. Create and Initialize Microgateway project 

    ```bash
    ## create a project and have the sample api file inside api_definition folder

    $ micro-gw init petstore
    $ cd api_definitions
    $ wget https://petstore.swagger.io/v2/swagger.json

    or 
    
    micro-gw init petstore -a https://petstore.swagger.io/v2/swagger.json

    ```

3. Build the project using adhoc command

    ```bash
    $ micro-gw build petstore --docker-image petstore:v1 --docker-base-image wso2/wso2micro-gw:3.2.1

    ```
3.1 

4. Generate API key

    ```bash
    TOKEN=$(curl -X get "[https://localhost:9095/apikey](https://localhost:9095/apikey)" -H "Authorization:Basic YWRtaW46YWRtaW4=" -k)
    ```

5. Invoke API

    ```bash
    curl -X GET "[https://localhost:9095/v2/pet/1](https://localhost:9095/v2/pet/1)" -H "accept: application/json" -H "api_key:$TOKEN" -k
    ```
