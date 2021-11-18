# croct-test
Feature: Sign in

	The screen / View that the user needs to fill the text boxes before trying to enter on his profile. It’s necessary to write the email and password before sign in 
	
	Rule: Users need to write the email and password registered
		
		Example: Sign in with the email that was registered
			Given I write my registered email
			And I write my registered password 
			When I try to sign in 
			Then I should see “Login complete” 

		Example: Sign in with the wrong email
			Given I write my wrong email 
			And I write my registered password
			When I try to sign in 
			Then I should see “That email is not registered” 

		Example: Sign in with the wrong password
			Given I write my registered email
			And I write my wrong password
			When I try to sign in
			Then I should see “That is not your password” 
