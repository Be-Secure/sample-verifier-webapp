# Sample Verifier Web application for DICE

The sample verifier web application demonstrates the functionality of DICE Verification Controller. 

## Prerequisites
Different components required for this demo are: 
- DICE Verification component 
- DICE Identity Wallet for Holder
- Credentials from sample-issuer-webapp  
- Verifiable Sample Web Application  (sample-verifier-webapp) 

DICE verification component is hosted at: https://futurebankvcauthcontroller.wiprobc.com

DICE Identity Wallet need to be installed on the mobile phone. The wallet is available on both Android and iOS platforms. 
 - On iOS, it be can downloaded from: [DICE ID - Apple playstore](https://apps.apple.com/in/app/dice-id/id1624858853)
 - On Android, the link is: [DICE ID - Apps on Google Play](https://play.google.com/store/apps/details?id=com.diwallet1)

To get credentials from sample issuer webapp, please refer to https://github.com/diceid/sample-issuer-webapp/blob/main/README.md

Sample verifier web application can be downloaded from here. 

## How to run
Once code is downloaded, follow the steps below to install and build the code:
1. change inside the directory sample-verififier webapp
2. build and Install webapp 
    - npm install 
    - npm run build 
    - npm start 
 
By default this will start the server on localhost:3000. Make sure that this url is mapped to public ip so that DICE Veirifier platform can access this and is able to return the result of verification back to the sample verifier webapp.

After the server has started with npm start, connect to http://localhost:3000 from your browser
  
## Flow Diagram  
The flow of Verifiable credential between these different parties is:<br>

![Flow between different parties](diagrams/flow_vc_auth.jpg)

## Customization 
Different steps user needs to go through to setup Verifiable credential are: <br>
1.	Configure Presentation request parameters with Verifier Controller:
PUT/POST https://futurebankvcauthcontroller.wiprobc.com/api/vc-config: This API can be used to configure the presentation request parameters. Holder will present proof in terms of these parameters. The id of this configuration need to be passed in the sample application
2.	Donwload sample verifier application and make the following changes:
   - Sample-verifier-webapp/src/vc_services/VC_AuthService.js 
      - Constants.clientRoot -> should point to the URL where sample verifier application is hosted. This URL should be accessible from Verifier controller 
      - userManager.settings.metadata.authorization_endpoint -> change pres_req_conf_id to the presentation request id you have created. If you haven’t created any new id, then the default id demo-access can be used.
3.	Install and build the application as mentioned before

