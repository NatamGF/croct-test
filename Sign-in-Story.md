Feature: Sign in

	The screen in which the user needs to fill out text boxes before trying to enter their profile. To proceed the user needs to inform their email and password.  
	
	Scenario: Sign in with the registered email and password
		Given I, the user, type in a registered email
		And I type in its registered password 
		When I try to sign in 
		Then I should see “Login complete” 

	Scenario: Sign in with the wrong email
		Given I, the user, type in the wrong email 
		And I type in its registered password
		When I try to sign in 
		Then I should see “Unregistered email” 

	Scenario: Sign in with the wrong password
		Given I, the user, type in a registered email
		And I type in an incorrect password
		When I try to sign in
		Then I should see “Incorrect password” 
	
	Scenario: Forgot Password
		Given I, the user, type in a registered email
		And I have forgotten its registered password
		When I click on “Forgot Password”
		Then I should see “Please inform the registered email and we’ll send you a message with instructions on how to reset your password” 

	Scenario: Remember me
		Given I, the user, type in a registered email
		And I type in its registered password
		When I check the box labeled “Remember me” 
		Then I should see the email and password already typed out when I reload the screen
	
	Scenario: Don’t want the email and password saved
		Given I, the user, type in a registered email
		And I type in its registered password
		When I don’t check the box labeled “Remember me” 
		Then I should not see the email and password typed out when I reload the screen

