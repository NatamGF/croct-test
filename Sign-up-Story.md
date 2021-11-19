Feature: Sign up
 
    The screen in which the user needs to fill out text boxes with their personal info and agree to the “Terms of Services” and the “Privacy Policy” before creating an account.     It’s necessary to type in their “First Name” and “Last name”, a valid email, a strong password and agree to the “Terms of Services” and the “Privacy Policy”. 

      Scenario: Don’t have an account
		      Given I, the user, don’t have an account
		      And I want to create an account
		      When I click on “Sign up” 
		      Then I should see the “Create Account” screen

	  Scenario: Creating an account
	      	      Given I, the user, click on “Sign up” on the “Sign in” screen
		      And I am redirected to the “Create Account” screen
		      And I type in my “First and Last name”
		      And I type in a valid email 
		      And I type in a valid password
		      And I check the box labeled “I agree to the Terms of Services and Privacy Policy” 
		      When I click on “Sign up” 
		      Then I should see “You created an account”

	  Scenario: Creating an account but with a invalid email
		      Given I, the user, click on “Sign up” on the “Sign in” screen
		      And I am redirected to the “Create Account” screen
		      And I type in my “First and Last name” 
		      And I type in an invalid email 
		      Then I should see “Please enter a valid email to create your account” in red under the email text field

	  Scenario: Creating an account with fictional First and Last name
		      Given I, the user, click on “Sign up” on the “Sign in” screen
		      And I am redirected to the “Create Account” screen 
	              And I type in a fictional “First and Last name”
		      And I type in a valid email 
		      And I type in a valid password
		      And I check the box labeled “I agree to the Terms of Services and Privacy Policy”
		      When I click on “Sign up” 
		      Then I should see “You created an account”

	  Scenario: Creating an account without Last name
                  Given I, the user, click on “Sign up” on the “Sign in” screen
                  And I am redirected to the “Create Account” screen 
	      	      And I type in only a “First name”
		      And I type in a valid email 
		      And I type in a valid password
		      And I check the box of  labeled “I agree to the Terms of Services and Privacy Policy”
		      When I click on “Sign up” 
		      Then I should see “Please inform your Last name”

	  Scenario: Creating an account without First name
                  Given I, the user, click on “Sign up” on the “Sign in” screen
                  And I am redirected to the “Create Account” screen  
		      And I type in only a “Last name”
		      And I type in a valid email 
		      And I type in a valid password
		      And I check the box labeled “I agree to the Terms of Services and Privacy Policy”
		      When I click on “Sign up” 
		      Then I should see “Please inform your First name”


 
  	Rule: The password needs to contain at least 8 characters, including numbers, symbols, uppercase and lowercase letters.

		      Example: Creating an account using a weak password
			         Given I, the user, click on “Sign up” on the “Sign in” screen
                             And I am redirected to the “Create Account” screen  
                             And I type in my “First and Last name”
		         	 And I type in a valid email
			         And I type in a weak password that doesn’t contain at least 8 characters, including numbers, symbols, uppercase and lowercase letters.
			         And I check the box labeled “I agree to the Terms of Services and Privacy Policy”
			         When I click on “Sign up” 
			         Then I should see “Passwords need to be at least 8 characters long, contain uppercase and lowercase letters, and have at least one number or symbol” 

		      Example: Creating an account with strong password
			         Given I, the user, click on “Sign up” on the “Sign in” screen
                             And I am redirected to the “Create Account” screen
                             And I type in my “First and Last name”  
			         And I type in a valid email
			         And I type in a strong password that contains at least 8 characters, including numbers, symbols, uppercase and lowercase letters.
			         And I check the box labeled “I agree to the Terms of Services and Privacy Policy”
			         When I click on “Sign up” 
			         Then I should see “You created an account”

		      Example: Creating an account and want to see the if the password is strong
			         Given I, the user, click on “Sign up” on the “Sign in” screen
                             And I am redirected to the “Create Account” screen
                             And I type in my “First and Last name”  
			         And I type in a valid email
			         And I type in a strong password that contains at least 8 characters, including numbers, symbols, uppercase and lowercase letters.
			         But I want to see my password after typing it in
			         When I click on the closed eye icon it should change to an opened eye icon 
			         Then I should see the revealed password


	  Scenario: Not checking the box labeled “I agree to the Terms of Services and Privacy Policy”
		      Given I, the user, click on “Sign up” on the “Sign in” screen
                  And I am redirected to the “Create Account” screen  
		      And I type in my “First and Last name”
		      And I type in a valid email
		      And I type in a valid password
		      But I didn’t check the box labeled “I agree to the Terms of Services and Privacy Policy”
		      When I click on “Sign up” 
		      Then I should see “Please agree to the Terms of Services and Privacy Policy”

	  Scenario: Want to read the Terms of Services
		      Given I, the user, click on “Sign up” on the “Sign in” screen
                  And I am redirected to the “Create Account” screen  
		      And I type in my “First and Last name”
		      And I type in a valid email
		      And I type in a valid password
		      But I want to read the Terms of Services to agree to it		
                  When I click on “Terms of Services”
		      Then I should be redirected to the “Terms of Services” screen

	  Scenario: Want to read the Privacy Policy
		      Given I, the user, click on “Sign up” on the “Sign in” screen
                  And I am redirected to the “Create Account” screen  
		      And I type in my “First and Last name”
		      And I type in a valid email
		      And I type in a valid password
		      But I want to read the Privacy Policy to agree to it		
                  When I click on “Privacy Policy”
		      Then I should be redirected to the “Privacy Policy” screen
