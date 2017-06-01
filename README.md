# Step wercker-oracle-accs-deploy
Wercker step to deploy application (Java, NodeJS, PHP, Python) to Oracle Application Container Cloud Service.

# Options

- `opc_user` user name for your Oracle Application Container Cloud account.
- `opc_password` password for your Oracle Application Container Cloud account.
- `rest_url` e.g.: `https://apaas.europe.oraclecloud.com/paas/service/apaas/api/v1.1/apps` Locate Oracle Application Container Cloud in the My Services console, click Details, and look at the REST Endpoint value.
- `domain` Name of the identity domain for the Oracle Application Container Cloud Service account.
- `application_name` Name of the application.
- `application_type` Runtime of the application (e.g.: java).
- `file` Name of the application archive (zip artifact).

# Example

	box: combient/java-mvn
	build:
	  steps:
	    # Build application
	    - script:
	        name: Maven install
	        code: mvn install
	deploy-accs:
	  steps:
	    # Deploy to Oracle Application Container Cloud
	    - peternagy/oracle-accs-deploy:
	        opc_user: $OPC_USERNAME
	        opc_password: $OPC_PASSWORD
	        rest_url: $REST_URL
	        domain: $IDENTITY_DOMAIN
	        application_name: springboot-accs-demo
			application_type: java
	        file: springbootdemo-0.0.1.zip
	        subscription_type: Hourly


This will copy the binary (zip artifact) to the storage container cloud service than deploy to application container cloud service.

# joshholt/oracle-accs-deploy

## 1.0.2

- update to storage auth tokens
- add subscription_type param for deployment purposes
- environment variable `WERCKER_ORACLE_ACCS_DEPLOY_SUBSCRIPTION_TYPE` typo

## 1.0.1

- environment variable `WERCKER_ORACLE_ACCS_DEPLOY_REST_URL` typo
 
## 1.0.0

- Readme.md update
- complete REST url instead of region part. Most likely in the future the url (e.g. version) can change.
- if application exists on application container cloud then updates the application

## 0.0.1

- Initial version

# License

The Universal Permissive License (UPL), Version 1.0
