Prerequisite: You need an AWS root account, which you would have created on Day 1.
Scenario: You want to create a new user who can only view and manage S3 buckets, but initially, you'll see what happens if no permissions are given.
Step 1: Log in as the Root User
•
Open your web browser and go to the AWS Management Console sign-in page.
•
Select "Root user" and enter your root account email address and password.
•
Click "Sign in" to log into your AWS account with full administrative privileges.
Step 2: Navigate to the IAM Service
•
Once logged in, in the search bar at the top of the AWS console, type "IAM" and select "IAM - Manage access to AWS resources". This will take you to the IAM Dashboard.
Step 3: Create a New IAM User (Authentication Only - No Authorization Yet)
•
In the IAM dashboard, navigate to "Users" in the left-hand menu.
•
Click the "Add users" button.
•
User details:
◦
For "User name," enter a name like test-user-501.
◦
Check the box for "Provide user access to the AWS Management Console".
◦
Select "I want to create an IAM user".
◦
For "Console password," choose "Auto-generated password" and ensure "Users must create a new password at next sign-in" is checked. This forces the user to set their own strong password upon first login.
•
Click "Next".
•
Permissions (Crucial for demonstration): Do NOT attach any policies or add the user to any group at this stage. Leave it as default. The purpose is to show that a user can authenticate but not authorize any actions.
•
Click "Next" to review.
•
Click "Create user".
•
Download Credentials: After the user is created, you will see a success message. Click "Download .csv" or copy the "Console sign-in URL," "Username," and "Password." You'll need these to log in as the new user.
Step 4: Log in as the New IAM User and Observe Limited Access
•
Sign out of your root AWS account.
•
Open a new incognito/private browser window or use the console sign-in URL provided for the IAM user.
•
Select "IAM user" and enter your AWS account ID (found in the sign-in URL or your root account settings) and the test-user-501 username.
•
Enter the auto-generated password you copied/downloaded.
•
You will be prompted to reset the password immediately. Enter the old password and create a new strong password.
•
Once logged in as test-user-501, try to access an AWS service, for example, search for "S3" in the console search bar and click on it.
•
Observation: You will likely see "Access Denied" errors or a message stating "You don't have permissions" when trying to list S3 buckets or create any resources. This demonstrates that while the user is authenticated (logged in), they are not authorized to perform any actions because no policies were attached.
Step 5: Add Permissions to the IAM User (Authorization)
•
Sign out of the test-user-501 account.
•
Log back in as your root user (or an administrative IAM user).
•
Go back to the "IAM" service.
•
Navigate to "Users" and click on test-user-501.
•
Click on "Add permissions".
•
Select "Attach policies directly".
•
In the search bar, type "S3" and select the AWS managed policy AmazonS3FullAccess. (This policy grants full control over S3 buckets, including listing, creating, and deleting).
•
Click "Next" to review.
•
Click "Add permissions".
Step 6: Log in as IAM User Again and Verify Access
•
Sign out of the root account.
•
Log back in as test-user-501 using your newly set password.
•
Navigate to the "S3" service.
•
Observation: You should now be able to see existing S3 buckets (if any) and also have the option to "Create bucket". Try creating a new bucket (remember S3 bucket names must be globally unique). This verifies that the user is now both authenticated and authorized to perform S3 actions.
Step 7: Demonstrate IAM Groups (for Efficient Management)
•
Sign out of test-user-501 and log back in as your root user.
•
Go to the "IAM" service.
•
Navigate to "User groups" in the left-hand menu.
•
Click "Create group".
•
Group details:
◦
For "User group name," enter DevelopmentGroup.
◦
Attach policies to the group: Search for and attach AmazonS3FullAccess and AmazonEC2FullAccess (or any other relevant policies).
•
Click "Create group".
•
Now, add the test-user-501 to this new group:
◦
Go to "User groups" and click on DevelopmentGroup.
◦
Click "Add users".
◦
Select test-user-501 (and any other users if you created them).
◦
Click "Add users".
•
Benefit of Groups: If in the future, all users in the DevelopmentGroup need access to another service (e.g., AWS Lambda), you simply attach the relevant policy to the DevelopmentGroup once, and all users within it (including test-user-501) will automatically inherit those permissions, saving significant manual effort.
This practical demonstration solidifies the understanding of how IAM users, policies, and groups work together to implement robust authentication and authorization within your AWS environment. Remember to be mindful of costs, especially when practicing with services that might incur charges, and to delete resources and users once you are done with your practice
