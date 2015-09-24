# Drupal-Ionic-AngularJS-API-Client
This repo is all about making clientside authed rest-calls easy to use.
(working version in branch 1.0.1)
# Features
## Show tour on first visit only
## Redirects for new and registered users
## Access control
## Authentication Service
## Drupal Services3 Resource-Services

#Workflow
- app lounge
- token (local storage or server)
- connect 
- start routing
???

#install
npm install cordova gulp ionic
##Dependencies
$ bower install ngCordova -save
$ bower install angular-cookie -save
$ bower install angular-messages -save

ipCookies

$ bower install https://github.com/BioPhoton/ng-drupal-7-services/tree/1.0.2 -save

##Plugins
$ cordova plugin add org.apache.cordova.network-information


##Drupal config

drupalIonicAngularJSAPIClient
	.config( function (  drupalApiConfig ) {
		drupalApiConfig.api_endpoint += 'v1/';
});

###account settings

###services

##Browser differences

##Session expiration
//https://api.drupal.org/api/drupal/includes!common.inc/function/drupal_http_request/7
- 401 UnauthorizedÃ¢â‚¬Å Ã¢â‚¬â€�Ã¢â‚¬Å The user is not logged in
- 403 ForbiddenÃ¢â‚¬Å Ã¢â‚¬â€�Ã¢â‚¬Å The user is logged in but isnÃ¢â‚¬â„¢t allowed access
- 419 Authentication Timeout (non standard)Ã¢â‚¬Å Ã¢â‚¬â€�Ã¢â‚¬Å Session has expired
- 440 Login Timeout (Microsoft only)Ã¢â‚¬Å Ã¢â‚¬â€�Ã¢â‚¬Å Session has expired

##Debugging
Wrong username or password => require email confirm checked in drupal
Projectname => Ensure this value has at most 32 characters
##???
 Any calls that use POST, PUT, or DELETE must now have a header key/value pair with "X-CSRF-Token" being the key, and the token retrieved from /user/token as the value to send along with the header key.

[https://www.drupal.org/node/2012982]https://www.drupal.org/node/2012982
 Description
This module enables you to expose an API to third party systems using REST, XML-RPC or other protocols.

The module doesn't sufficiently verify writing requests (POST, PUT, DELETE) with session cookie authentication, thereby exposing a Cross Site Request Forgery vulnerability.

This vulnerability is mitigated by the fact that session based authentication must be enabled for an endpoint.

Homepage is tour
If firsVisit is true then homepage is register
If HasLoggedIn is true then homepage is login
If user is authed homepage is porfile

Tokens
After register if successful we log the user in automatically. 
Tokens and cookies only apply to logging in or system connect requests.

Cookies
On login we save a cookie with the name of the session_name returned in the logged in user data. 

Therefore the cookie saved is $cookie[session_name] = session_id 

This cookie is used to validate the session on drupal when doing a authenticated request
Angularjs *does not* automatically save cookies and use them when doing requests
Therefore on login we need to save the cookie and use it when doing requests.
*Chrome does this automatically, itÃƒÂ¢Ã¢â€šÂ¬Ã¢â€žÂ¢s for Safari and Firefox and for iPhones

Tokens
