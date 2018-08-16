# ObAIoT_GASAPI
A collection of useful Google Apps Script API related to Google Serives. You may add the API in you Apps Script project or call the API by web service.<br/>
First of all, a Gmail verifier is present for validating if a email address is a valid "Gmail".

# Setup
* Google Apps Script API<br/>
This library is already published as an Apps Script API, making it easy to include in your project. To add it to your script, do the following in the Apps Script editor:
1. Click on the menu item "Resources > Libraries..."
In the "Add a Library" text box, enter the project key ```MSNSZfBH_WHXkkG_V3T5W5eFrpvyrbQzU``` and click the "Add" button.
Choose a version in the dropdown box (to pick the latest version).
Click the "Save" button.
2. Enable the "Drive API" in both
"Resources > Advanced Google Services..." &
"Resources > Cloud Platform project...<br/><br/>

* Web Service<br/>
POST to API endpoint:<br/>
https://script.google.com/macros/s/AKfycbxswDaJlXbeV9dzcm8dTHLqGunlBeSOoiKtgD5rGQoRpwItAa9w/exec

# Getting Started
Response is a JSON object: <br/> {"success":true,"gmail":"contact@obaiot.com","isValidGmail":true} <br/>
success [bool]: true for API call success or false for failure,  <br/>
gmail [string]: the gmail to validate,  <br/>
isValidGmail [bool]: indicates if a valid Gmail address  <br/>

* Google Apps Script API
```javascript
var gmailVerifierApi = new ObAIoTGASAPI.cGmailVerifier();
var response = gmailVerifierApi.validate($Gmail_to_validate);
```
* Web Service:<br/>
Example is in javascript<br/> 
```javascript
 try {
    var webHookUrl = 'https://script.google.com/macros/s/AKfycbxswDaJlXbeV9dzcm8dTHLqGunlBeSOoiKtgD5rGQoRpwItAa9w/exec';
    var payload = {
      "API": "gmailVerifier.validate",
      "gmail" : $Gmail_to_validate,  
    }
    
    var options =  {
      "method" : "post",
      "contentType" : "application/json",
      "payload" : JSON.stringify(payload)
    };
    
    var response = UrlFetchApp.fetch(webHookUrl, options); 
    var responseCode = response.getResponseCode();
    if (responseCode == 200) {
      return response;
    }
    else {
      Logger.log('post to ObAIoT_GASAPI failed, error code = ' + responseCode);
      return response;
    }
  }
  catch (ex) {
    Logger.log('post to ObAIoT_GASAPI failed, ex = ' + ex);
  }
```
