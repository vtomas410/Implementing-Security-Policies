# Implementing-Security-Policies

**Prerequisites:**

need to have installed.

- Windows Server on a virtual Machine
- Active Directory Domain Services
- Group Policy Management Console
- Windows Pro or Enterprise client

---

# **Activity 1: Password Policy Configuration**

Configure and enforce a strong password policy for AD users. Setting policies for Minimum Password Length, Password Complexity, Password Age. 

- Windows minimum: 8 characters
- Strong password : 12 characters

Step 1: Open group policy management software. 

Step 2: Create a new Group Policy Object or edit default domain policy.

<img width="1066" height="808" alt="1 default Domain Policy Edit" src="https://github.com/user-attachments/assets/7b21d2bc-1126-48e1-b8dd-fe799778d5b2" />


Step 3: Right click “Default Domain Policy” → select computer configuration → Select policies → Click Windows Settings → Select Security settings → select Account Policies → Then finally select Password policies.

<img width="1259" height="909" alt="2 Password Policy - Password Length Edit" src="https://github.com/user-attachments/assets/d8d54446-e9bf-484e-b765-f76e20b11b41" />


Step 4: This is where you can set different policy settings. Change these settings.

- Enforce Policy History: 4 Passwords Remembered
- Maximum Password age: 60 days
- Minimum password length: 12 characters
- Password must meet Complexity requirements: “Enabled”

This is how you configure and enforce strong password policy for AD users.

<img width="798" height="556" alt="3 Password Policy Update" src="https://github.com/user-attachments/assets/fb94fdb1-5617-42d8-bbd4-775c5ab3d267" />


 **Verifying policy by testing**

Step 1: Create a test user account and attempt to create a weak password to see if the policy was enforced.

<img width="445" height="386" alt="4 Create New user to Test Policy " src="https://github.com/user-attachments/assets/4c6fbb4b-6aa2-46c5-936e-acec2a14f939" />


Step 2: make sure to check user must change password at next logon


Step 3: log into the new account.

<img width="1027" height="757" alt="5 Change Password next login" src="https://github.com/user-attachments/assets/d9f2559c-0e07-4f19-a5ba-cadcb865ef22" />


Step 4: The windows computer will ask to change password.

<img width="612" height="695" alt="6 Successful Login Policy " src="https://github.com/user-attachments/assets/9ac8914a-4053-42ae-aa14-3cb6e014e11a" />


Step 5: Type an easy password. “1,2,3,4,5”

Step 6: you should get this error.

“Unable to update the password. The value provided for the new password, does not meet the length, complexity, or history requirements of the domain.

Step 7: change to a password that meets all requirements. 

Step 8: check it and it should change the password.

---

# **Activity 2: Account Lockout Policy Configuration**

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

<img width="901" height="570" alt="7 Account Login Fails Attempts - Policy Change " src="https://github.com/user-attachments/assets/fbced35f-a8cc-438f-a035-e6d1e0870807" />

**Verifying policy by testing**

Test using a user account. Intentionally fail 3 logon attempts to verify the account gets lockout.

It should get lockout, meaning our policy worked.

<img width="549" height="498" alt="8 Successful Account Policy Change - Login Fail Attempts " src="https://github.com/user-attachments/assets/7bb0da9d-b7d2-4d43-91d6-5a7016a4e49c" />

---

# **Activity 3: User Rights Assignment**

Assign and restrict user rights to enhance security.

- Role Based Access
- Deny Logon Locally
- Restrict remote desktop Acess

Step 1: Open Group policy Management console.

step 2: Create a new GPO. Name it “User Rights”

Step 3: Expand Group Policy Objects

Step 4: Step 3: Right click “User Rights” → select computer configuration → Policies → Windows Settings → Security Settings →Local Policies →User Rights Assignment.

<img width="1043" height="776" alt="9 User Rights Creation Policy" src="https://github.com/user-attachments/assets/8cd3916f-ebeb-499d-bd31-d77727c29135" />

Step 5: This is where you can set different policy settings. Change these settings.

- Deny Logon Locally → Define these policy settings → Add User or Groups → Browse → “HR Department” → ok
- Allow Log on through remote desktop services Properties → Define these policy settings → Add User or Groups → Browse → “HR Department” → ok


<img width="1018" height="640" alt="10 Deny log on as Update Window" src="https://github.com/user-attachments/assets/cb10ea12-ef90-455c-b7fc-91a8b3df3fc7" />

<img width="420" height="265" alt="11 allow Logon through Remote Desktop" src="https://github.com/user-attachments/assets/fa15db9a-5e6b-48ca-944d-29fb2842c763" />


**Verifying policy by testing**

Testing Deny log on locally policy. Use a regular user that is not part of the IT or Hr group. This message should appear.

Testing Log On through Remote Desktop. Login as a regular user, not as system admin. Open Remote desktop connection. Enter name of server. Click connect. This message should pop up, because we are not allowed to use “remote dektop” with a regular user account.

<img width="557" height="137" alt="Connection denied remote desktop" src="https://github.com/user-attachments/assets/9e1075ce-9a54-4561-86dd-abccea3a6776" />

---

# **Activity 4: Implementing Fine Grained Password Policies**

Apply different password policies to different groups of users.

Scenario: The organization wants to apply stricter password policies to administrative accounts while allowing standard users to have less stringent requirments.

- Fine Grained Password policys

Step 1: Open Active Directory Administrative Center

Step 2: Domain Name → Password settings container → Create a new → password settings object 

<img width="560" height="452" alt="12 Fine Grain Password" src="https://github.com/user-attachments/assets/224e66ab-e96c-45b7-8874-39e3a0a183b9" />


Step 3: Admin Password Policy for name. Type in Precedence “1”. 

Step 4: Change Minimum Password length to “15”. Enforce password history to “5”.

Step 5: At the bottom click → add groups → select IT admins.

<img width="861" height="562" alt="13 create Password Settings" src="https://github.com/user-attachments/assets/a6ecb64f-6e9e-4d9f-9283-83bd80253daf" />


Step 6: Click Done.

Step 7: Create new password setting. 

Step 8: Name it “Userpasswordpolicy” and Precedence to “2”.

Step 9: Change Minimum Password length to “15”. Enforce password history to “5”.
<img width="940" height="650" alt="15 User Password Policy " src="https://github.com/user-attachments/assets/41ef5413-046b-4f44-b25d-2a157adb8329" />

Step 10: At the bottom click → add groups → select HR admins.

<img width="738" height="507" alt="14 Directly Applys to HR department" src="https://github.com/user-attachments/assets/6d6de0cc-bfc3-4332-aecf-6ac6db12d3d0" />


Step 11: Click Done. Successful Completion.

<img width="754" height="531" alt="16 Successful Completion " src="https://github.com/user-attachments/assets/11db1f30-5e3e-4eaf-a4b2-84760b84e358" />

