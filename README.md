# Implementing Security Policies | Fine-Grained Passwords

Prerequisites:

need to have installed.

- Windows Server on a virtual Machine
- Active Directory Domain Services
- Group Policy Management Console
- Windows Pro or Enterprise client

---

Activity 1: Password Policy Configuration 

Configure and enforce a strong password policy for AD users. Setting policies for Minimum Password Length, Password Complexity, Password Age. 

- Windows minimum: 8 characters
- Strong password : 12 characters

Step 1: Open group policy management software. 

Step 2: Create a new Group Policy Object or edit default domain policy.

Step 3: Right click “Default Domain Policy” → select computer configuration → Select policies → Click Windows Settings → Select Security settings → select Account Policies → Then finally select Password policies.

Step 4: This is where you can set different policy settings. Change these settings.

- Enforce Policy History: 4 Passwords Remembered
- Maximum Password age: 60 days
- Minimum password length: 12 characters
- Password must meet Complexity requirements: “Enabled”

This is how you configure and enforce strong password policy for AD users.

 **Verifying policy by testing**

Step 1: Create a test user account and attempt to create a weak password to see if the policy was enforced.

Step 2: make sure to check user must change password at next logon

Step 3: log into the new account.

Step 4: The windows computer will ask to change password.

Step 5: Type an easy password. “1,2,3,4,5”

Step 6: you should get this error.

“Unable to update the password. The value provided for the new password, does not meet the length, complexity, or history requirements of the domain.

Step 7: change to a password that meets all requirements. 

Step 8: check it and it should change the password.

---

Activity 2: Account Lockout Policy Configuration

Configure an account lockout policy to protect against brute force attacks. The higher the threshold, the higher the probability for a successful brute force attack.

- Password Threshold
- Password Lockout Duration

Step 1: Open Group policy Management console.

step 2: Create a new GPO or edit default domain policy.

Step 3: Step 3: Right click “Default Domain Policy” → select computer configuration → Policies → Windows Settings → Security Settings → Account Policies → Account Lockout Policy.

Step 4: This is where you can set different policy settings. Change these settings.

- Account Lockout Duration: 30 minutes
- Account lockout Threshold: 3 Invalid logon attempts
- Reset Account Lockout Counter after: 30 minutes

**Verifying policy by testing**

Test using a user account. Intentionally fail 3 logon attempts to verify the account gets lockout.

It should get lockout, meaning our policy worked.

---

Activity 3: User Rights Assignment

Assign and restrict user rights to enhance security.

- Role Based Access
- Deny Logon Locally
- Restrict remote desktop Acess

Step 1: Open Group policy Management console.

step 2: Create a new GPO. Name it “User Rights”

Step 3: Expand Group Policy Objects

Step 4: Step 3: Right click “User Rights” → select computer configuration → Policies → Windows Settings → Security Settings →Local Policies →User Rights Assignment.

Step 5: This is where you can set different policy settings. Change these settings.

- Deny Logon Locally → Define these policy settings → Add User or Groups → Browse → “HR Department” → ok
- Allow Log on through remote desktop services Properties → Define these policy settings → Add User or Groups → Browse → “HR Department” → ok

**Verifying policy by testing**

Testing Deny log on locally policy. Use a regular user that is not part of the IT or Hr group. This message should appear.

Testing Log On through Remote Desktop. Login as a regular user, not as system admin. Open Remote desktop connection. Enter name of server. Click connect. This message should pop up, because we are not allowed to use “remote dektop” with a regular user account.

---

Activity 4: Implementing Fine Grained Password Policies

Apply different password policies to different groups of users.

Scenario: The organization wants to apply stricter password policies to administrative accounts while allowing standard users to have less stringent requirments.

- Fine Grained Password policys

Step 1: Open Active Directory Administrative Center

Step 2: Domain Name → Password settings container → Create a new → password settings object 

Step 3: Admin Password Policy for name. Type in Precedence “1”. 

Step 4: Change Minimum Password length to “15”. Enforce password history to “5”.

Step 5: At the bottom click → add groups → select IT admins.

Step 6: Click Done.

Step 7: Create new password setting. 

Step 8: Name it “Userpasswordpolicy” and Precedence to “2”.

Step 9: Change Minimum Password length to “15”. Enforce password history to “5”.

Step 10: At the bottom click → add groups → select HR admins.

Step 11: Click Done.
