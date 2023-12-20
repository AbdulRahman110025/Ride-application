# Ride-application
In this project we will going to build serverless web Application using aws service.
i have used codecommit for git repository platform.
I have used amplify to create static website . so amplify is basically manage all the web contents and will allow the users to access your web application through URL exposed by amplify. so you dont need to buy your domain for your application .
i have installed aws CLI in this so that i can bring all the files related to the project
write AWS configure and enter access key and security key of IAM user
after that write " git clone "url"" it would tell you that your repository is empty
to get access to web contents there is the publicly available s3 bucket and for that you need to write tghe following command:
               aws s3 cp s3://wildrydes-us-east-1/WebApplication/1_StaticWebHosting/website ./ --recursive
then add , commit and push the file in repo. 

Now go to the AWS management console and type AMplify in search bar . we have to host out application HEADER so click on get started under mentioned header.
Once you have hosted your website on amplify click on the generated link tp accwess your website.
now you have created your STATIC WEBSITE.


AUTHENTICATION:
now that we have build our static website , now we want our users who will acces our website to authenticate themselves so for that we will use amazomn cognito. Now , we will depoy pages for costomers to register ,verify, sign in .
after users refgister , cognito will send verification code to the user email they provided.
After users have a confirmed account (either using the email verification process or a manual confirmation through the console), they will be able to sign in. When users sign in, they enter their username (or email) and password. A JavaScript function then communicates with Amazon Cognito, authenticates using the Secure Remote Password protocol (SRP), and receives back a set of JSON Web Tokens (JWT).


=> create cognito user pool and integrate it with the app
Amazon Cognito provides two different mechanisms for authenticating users. You can use Cognito User Pools to add sign-up and sign-in functionality to your application or use Cognito Identity Pools to authenticate users through social identity providers such as Facebook, Twitter, or Amazon, with SAML identity solutions, or by using your own identity system. For this module you'll use a user pool as the backend for the provided registration and sign-in pages.
In the Amazon Cognito console, choose Create user pool.
On the Configure sign-in experience page, in the Cognito user pool sign-in options section, select User name. Keep the defaults for the other settings, such as Provider types and do not make any User name requirements selections. Choose Next.
On the Configure security requirements page, keep the Password policy mode as Cognito defaults. You can choose to configure multi-factor authentication (MFA) or choose No MFA and keep other configurations as default. Choose Next.
On the Configure sign-up experience page, keep everything as default. Choose Next.
On the Configure message delivery page, for Email provider, confirm that Send email with Amazon SES - Recommended is selected. In the FROM email address field, select an email address that you have verified with Amazon SES, following the instructions in Verifying an email address identity in the Amazon Simple Email Service Developer Guide.
Note: If you don't see the verified email address populating in the dropdown, ensure that you have created a verified email address in the same Region you selected at the beginning of the tutorial. 
 On the Integrate your app page, name your user pool: WildRydes. Under Initial app client, name the app client: WildRydesWebApp and keep the other settings as default.
On the Review and create page, choose Create user pool.
On the User pools page, select the User pool name to view detailed information about the user pool you created. Copy the User Pool ID in the User pool overview section and save it in a secure location on your local machine. 
Select the App Integration tab and copy and save the Client ID in the App clients and analytics section of your newly created user pool.





==> update the website config file:
The js/config.js file contains settings for the user pool ID, app client ID and Region. Update this file with the settings from the user pool and app you created in the previous steps and upload the file back to your bucket.

From your local machine, open the wildryde-site/js/config.js file in a text editor of your choice.
Update the cognito section of the file with the correct values for the User pool ID and App Client ID you saved in Steps 8 and 9 in the previous section. The userPoolID is the User pool ID from the User pool overview section, and the userPoolClientID is the App Client ID from the App Integration > App clients and analytics section of Amazon Cognito. 
The value for region should be the AWS Region code where you created your user pool. For example, us-east-1 for the N. Virginia Region, or us-west-2 for the Oregon Region. If you're not sure which code to use, you can look at the Pool ARN value on the User pool overview. The Region code is the part of the ARN immediately after arn:aws:cognito-idp:.
