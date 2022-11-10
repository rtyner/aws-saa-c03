- Complex projects and businesses use multiple AWS accounts
- AWS account - **container** for identities and AWS resources
	- Identities = users
- Root users are per account
- Root user has full control over the account and resources
	- cannot be restricted 
- Can set alternate contacts for different functions of the account
	- ![[Pasted image 20221029110042.png | 1000]]
- AWS Organization - connects AWS accounts

### Security of AWS Accounts
- IAM can be used to create identities within the AWS account
	- IAM users, groups, roles
	- Can be given granular permissions
	- Cross account permissions are possible
- AWS accounts can contain the impact of admin errors and bad actors
- **Use separate accounts for separate things, teams, products (test, dev, prod)**
- By default all external access to an AWS account and resources are denied except for the root account
- External identities can be granted access if needed

### Course AWS Accounts
- Types of accounts created
	- General account - services+cantrll-general@rtyner.com
	- Production account - services+cantrll-prod@rtyner.com
- Settings
	- 2FA
	- Budget
	- IAM User and Role Access to Billing Information
	- IAM user
- MFA
	- Factors - pieces of evidence which prove identity
		- Knowledge - something you know, UN/PW
		- Possession - something you have, MFA device/app
		- Inherent - something you are, biometrics
		- Location - Physical location (GPS), or specific network