

Prerequisites:
• You should have an active AWS account.
• You should have an EC2 instance already running from previous lessons (e.g., a Ubuntu machine)

Practical 1: Logging into an EC2 Instance via AWS UI (Console)
Navigate to EC2 Dashboard > Select Running Instance
Click Instance ID: Click on the "Instance ID" of your running EC2 instance
Connect to Instance: On the instance details page, locate and click the "Connect" button
Verify Connection: Once connected (a terminal-like interface will appear in your browser).

Practical 2: Installing a Recommended Terminal for Windows
Open your web browser and search for "PuTTY", "MobileXterm", or "NoMachine".
Go to the official website of your preferred terminal.
Download the installer (e.g., MSI for PuTTY, installer for MobileXterm).
Follow the installation wizard steps (usually "next, next, finish")

Practical 3: Logging into an EC2 Instance via Terminal (CLI)
Open Your Terminal: Launch the terminal application you installed (or your default terminal on Linux/Mac).
Get Public IP Address: Go back to your AWS EC2 Console, select your running instance, and copy its "Public IPv4 address". This IP is used for external connections from your laptop.

Attempt SSH (Initial): In your terminal, type SSH Ubuntu@<Public_IP_Address> (replace <Public_IP_Address> with the actual IP). Press Enter.
Expected Result: For the first connection, it will ask "Are you sure you want to continue connecting (yes/no/[fingerprint])?". Type yes and press Enter. You will likely then get a "Permission denied (publickey)" error.
Reason: You haven't provided the key-value pair (.pem file) for authentication.

Attempt SSH with Key-Value Pair: Type SSH -i <Path_to_your_key_file.pem> Ubuntu@<Public_IP_Address> (replace <Path_to_your_key_file.pem> with the actual path to your .pem file, e.g., /Users/youruser/Downloads/test11.pem). Press Enter.
Expected Result: You will likely get an error stating "Permissions are too open" or similar, indicating the .pem file's permissions are too broad.
Reason: .pem files contain sensitive information and must have restricted permissions (only readable by the owner) to prevent unauthorized access.

Change .pem File Permissions: In your terminal, type chmod 600 <Path_to_your_key_file.pem> and press Enter. This command sets the file permissions so only the file owner can read and write to it.

Retry SSH with Key-Value Pair (Success Expected): Press the "Up Arrow" key in your terminal to recall the previous SSH -i command, then press Enter.
Expected Result: You should now successfully log into your EC2 instance. Your terminal prompt will change to something like Ubuntu@ip-xxx-xx-xx-xx:~.

Verify Connection:
Type ls and press Enter. You should see the example file you created earlier via the UI.
Type touch example2 and press Enter to create another file. Then type ls again to confirm example2 is listed.
(Optional): You can go back to the AWS UI connection (Practical 1) and verify example2 is visible there as well


Practical 4: Authenticating AWS CLI (aws configure)
This step links your AWS CLI to your AWS account using secure credentials.

Generate Access Keys: Log in to your AWS Management Console.
In the top-right corner, click on your user name (e.g., "seemon").
From the dropdown menu, select "Security Credentials".
◦On the "Security credentials" page, scroll down to the "Access keys" section.
Click "Create access key".
Read the warning about best practices, then click "I understand the above recommendation and want to proceed to create an access key." followed by "Create access key".

CRITICAL: Immediately copy the "Access key ID" and "Secret access key" that are displayed. Store them securely (e.g., in a password manager or a temporary secure note). The secret key will not be shown again after you leave this page.
Click "Done".

*****Configure AWS CLI: Open your terminal.
Type aws configure and press Enter.
AWS Access Key ID: Paste the Access Key ID you copied from the AWS console and press Enter.
AWS Secret Access Key: Paste the Secret Access Key you copied from the AWS console and press Enter.
Default region name: Enter your preferred default AWS region (e.g., us-east-1 for North Virginia) and press Enter.
Default output format: Type json and press Enter.
Result: Your AWS CLI is now authenticated with your AWS account.


Practical 5: Interacting with AWS Services using CLI (Examples)
Now you can use the CLI to manage your AWS resources.

List S3 Buckets: In your terminal, type aws s3 ls and press Enter.
Expected Result: A list of all S3 buckets in your default region (or globally, for S3) should be displayed, matching what you see in the AWS S3 Console.

Create an S3 Bucket (Optional):
In your terminal, type aws s3 mb s3://<Your_Unique_Bucket_Name> (replace <Your_Unique_Bucket_Name> with a globally unique name, e.g., my-unique-test-bucket-12345). Press Enter.
Expected Result: A message indicating the bucket was successfully created. You can verify this by running aws s3 ls again or by checking the AWS S3 Console.



