---
layout: post
title:  "How To Upload A File To Firebase Store"
date:   2021-04-01 10:20:30 -0000
categories: firebase file upload
---

### Why?

Let's say you want your users to upload a file to your web site. How would you do it. 

It sounds pretty easy, isn't it? However, I was out of web development for a while and found it a bit challenging.


### File Upload



### Authentication


#### New User Sign Up use case.

1. New User that wants to sing up clicks on a `sign up` button and is presented with the screen collecting User info:

- First Name
- Last Name
- Address
- Phone #
- E-mail address
- Password

Note: All fields are required and wll be client side validated.

2. User clicks on `Submit` (or `Sign up`) button. System saves user data and sends email to user with the link to complete the sign up process.

3. User receives email with the link to complete the sign up process and clicks on the link. Link opens page in a browser and sends email validation request. System completes the sign up process and respond with the `Success` message. Message will instruct user to sign in into the syetem now with saved credentials.

4. In case system responds with `Failure` status/message, the signup process will need to be started over with the `Sighn up` screen. If user credentials have been saved, system will suggest to login with the saved credentials or reset the password.


#### Existing User Login with email use case.

1. User clicks on `Login` button. Browser redirects (or pops up) to the screen with login options. `Login with Email` must be one of the available options.

2. User clicks on the `Login with Email` button. System will redirect (or pop up) to another screen with User ID/email and password.

3. User enters credentials and clicks `Submit` (or `Login`) button. System will validate the credentials and respond with either `Success` or ` Failure` response.

4. System responds with the `Failure` response. There should be error message displayed to teh user and the option to login again. Also, system should check number of attemts.
- System should add Capture to all login attempts after 3 failed ones.
- System should suggest to reset password after 5 failed attempts to login.

5. System responds with `Success` and access token. Access token should be stored safely in broweser (alternativley we might need to re-authenticate to get new token), becaue access token will need to be passed to all concequitive API calls.
Note: We assume that access token refresh is handled authomatically by the Firebase Authentication. Maybe access token is also handled automatically by the system. We need to test it.


#### Password reset use case.

1. Once we reached max number of login failed attempts, system will pesent the option to reset password.

2. User clicks on the `Reset Password` button/link. System will send user email (to the address stored during sign up process) with the link to reset the password. 

3. User goes to the email and clicks on the `Reset Password` link. System presents user with the screen in the browser to enter new password.

4. User enters new password and clicks `Submit` (or `Reset Password`) button. System updates the password and replies with the `Success` message. From this point user can go back to the login screen and login with new password.

5. If system responds with `Failure` message, process need to be started over. User will need to click on the link in the email.


#### Forgot my id/email use case (we may not need to support this, at least not at the beginning:

1. if user forgot id/email address, user will click on the `Frgot my ID` link. System will redirect to the `Forgot my ID` screen.

2. User will type email address and click on `Submit` button. Sytem replies with the message if ID has been found or not. In case ID has been found, user can use `Password Reset` functuanality to reset the password through email link. If ID has not been found, user will have to create new account.

3. Paid users have to co through customer service to recover frgotten ID or recover the account. 


#### Sign-up and Login use case

1. User enters email and clicks `Next` button. System checks if email exists and changes the UI to:

	a. `Create Account` (or `Sign Up`) screen, if email is not found.

	b. `Login` screen, if email is found.

2. Login screen asks for password as a next step. User envers the password and ckicks `Login` button. System either return Success if password matches or Failure if not.

3. Create account screen asks for additional user info and password. User fills in all the required fields and clicks `Submit` or `Sign Up` button. System creates an account.


It probably will have some code snippets like this:

{% highlight js %}

function print_hi(name) {
  console.log("Hi, #{name}")
}

console.log('Tom')
=> prints 'Hi, Tom' to STDOUT.

{% endhighlight %}
