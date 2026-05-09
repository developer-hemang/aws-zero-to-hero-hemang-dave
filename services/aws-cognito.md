# AWS Cognito Guide 


## Table Of contents 

* [What Is Cognito](#what-is-cognito)






# What Is Cognito ?

AWS Cognito is a fully managed authentication, authorization, and user management service provided by AWS.

### It helps developers:
- Add sign-up/sign-in functionality
- Manage users securely
- Implement authentication and authorization
- Integrate with social login providers
- Secure APIs and applications
- Generate temporary AWS credentials

Cognito removes the need to build authentication systems manually.



### Real-Life Definition

Suppose you build:
- E-commerce app
- Banking app
- Food delivery app
- SaaS application
- Mobile application


### Users need:

- Registration
- Login
- Forgot password
- MFA
- OTP verification
- Google/Facebook login
- Session management
- Access control

Instead of building all these manually, AWS Cognito provides them as managed services.


## Main Components of Cognito

### AWS Cognito has 2 major components:

| Component      | Purpose                       |
| -------------- | ----------------------------- |
| User Pools     | Authentication (login system) |
| Identity Pools | Authorization (AWS access)    |



# 1. Cognito User Pool

User Pool is a user directory that stores users and handles authentication.

Create a serverless database of user for your web & mobile apps.

### Think of it like:

```bash
"Managed login system by AWS"
```


### It manages:

- Simple Login/Signup: Username (or email) / password combination
- PAssword Reset
- Email & Phone Number Verification
- Multi Factor authentication (MFA)
- Federated Identities: users from Facebook, Google, SAML…
- Feature: block users if their credentials are compromised elsewhere
- Login sends back a JSON Web Token (JWT)



# User Pool Features

### 1. User Registration
Users can register with:
- Email
- Phone number
- Username

```js
Email: test@gmail.com
Password: MyPass@123
```

### 2. Authentication

Supports:
- Username/password login
- OTP login
- Passwordless authentication
- MFA


### 3. Multi-Factor Authentication (MFA)

Extra security layer.
Supported MFA:
- SMS OTP
- TOTP apps (Google Authenticator)

Example flow:

```bash
1. Enter username/password
2. Receive OTP
3. Verify OTP
4. Login success
```

### 4. Email & Phone Verification

Automatically sends:
- Verification email
- SMS verification code


### 5. Password Policies

You can configure:

- Minimum length
- Special characters
- Password expiry
- Password history

### 6. Social Login Federation

Supports:

| Provider |
| -------- |
| Google   |
| Facebook |
| Apple    |
| Amazon   |
| SAML     |
| OIDC     |

#### Example:

```bash
Login with Google
```

# 7. JWT Token Generation

### After login Cognito generates:

| Token         | Purpose             |
| ------------- | ------------------- |
| ID Token      | User identity       |
| Access Token  | API authorization   |
| Refresh Token | Generate new tokens |


Example JWT Flow

```bash
User Login
   ↓
Cognito validates credentials
   ↓
Returns JWT tokens
   ↓
Frontend sends Access Token to API Gateway
   ↓
API Gateway validates token
   ↓
Lambda executes
```

# 2. Cognito Identity Pool

Definition

Identity Pool provides:

Temporary AWS credentials for users

It allows users to access AWS services securely.




# Why Identity Pool Needed?

Suppose user uploads image directly to S3.

### Without Identity Pool:

### ❌ You cannot expose AWS IAM credentials to frontend.

### With Identity Pool:

### ✅ Cognito gives temporary limited credentials.


Example

Mobile app user uploads image to S3:

```js
User Login
   ↓
Cognito User Pool authenticates
   ↓
Identity Pool generates temporary AWS credentials
   ↓
User uploads image to S3
```


| AWS Service | Usage                  |
| ----------- | ---------------------- |
| API Gateway | Secure APIs            |
| Lambda      | Backend processing     |
| IAM         | Access control         |
| S3          | File upload            |
| AppSync     | GraphQL authentication |
| CloudFront  | Secure web apps        |
| ALB         | Authentication         |
| EventBridge | Authentication events  |
| SES         | Email verification     |
| SNS         | SMS OTP                |
| CloudWatch  | Monitoring             |
| WAF         | Security protection    |




# Services Commonly Used with Cognito


COgnito USer pool lamda triggers

user pool flow operations description for each operations mention all event triggers 


hosted authentication UI

Hosted UI on custom domain with acm

Adaptive Authentication 

