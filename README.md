# ObAIoT_GASAPI
A collection of useful Google Apps Script API and web services
First of all, a Gmail verifier is present for validating if a email address is a valid Gmail.

# Setup
This library is already published as an Apps Script, making it easy to include in your project. To add it to your script, do the following in the Apps Script editor:
1. Click on the menu item "Resources > Libraries..."
In the "Add a Library" text box, enter the project key ```MSNSZfBH_WHXkkG_V3T5W5eFrpvyrbQzU``` and click the "Add" button.
Choose a version in the dropdown box (to pick the latest version).
Click the "Save" button.

#Getting Started
```javascript
var gmailVerifierApi = new ObAIoTGASAPI.cGmailVerifier();
var response = gmailVerifierApi.validate(gmail);
```
response is a JSON object: {"success":true,"gmail":"contact@obaiot.com","isValidGmail":true} <br/>
success: true for API call success or false for failure, 
gmail: the gmail to validate
isValidGmail: indicates if a valid Gmail address
