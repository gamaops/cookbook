# Identity API

The identity API exposes services related to authentication.

## Errors

Code                | Meaning
--------------------|----------------------------------------------------------------------
INVALID_PHONENUMBER | When you try to send an invalid phone number to the API
ALREADY_SIGNED_UP   | When the identity that you're trying to sign up has already singed up
WAIT_BEFORE_SIGN_UP | When the API throthles the sign up request
SIGN_UP_NOT_FOUND   | When the requested sign up ID doesn't exist

## SignUpService.SignUpLead

### Request 

Example payload:

```json
{
  "signUpLead": {
    "validationChannel": 0,
    "name": "John Doe",
    "email": "john.doe@gamaops.com"
  }
}
```

And with cellphone as validation channel:

```json
{
  "signUpLead": {
    "validationChannel": 1,
    "name": "John Doe",
    "cellphone": "+55 (11) 91234-5566"
  }
}
```

### Response

And the response will be:

```json
{
  "signUpId": "a1315f09-ebb7-46f1-a934-45b3b3ee3d38"
}
```

### Description

The validation channel is used to validate the sign up request, we have to create an authentication to clients on the sign up process, this is why we separated the sign up from the registry process. And the validation code sent to the choosen channel can be used to generate an identity token using the method described bellow:

## SignUpService.ValidateSignUp

### Request

```json
{
  "signUpId": "a1315f09-ebb7-46f1-a934-45b3b3ee3d38",
  "validationCode": "3143FA"
}
```

### Response

```json
{
  "success": true,
  "identityToken": "eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCJ9.eyJuYW1lIjoiSm9obiBEb2UiLCJpYXQiOjE1Njg5MDQ4MzgsImV4cCI6MTU2ODkwNTQzOCwiYXVkIjoiaHR0cDovL3NpZ251cC5nYW1hb3BzLmNvbSIsImlzcyI6Imh0dHA6Ly9nYW1hb3BzLmNvbSIsInN1YiI6ImExMzE1ZjA5LWViYjctNDZmMS1hOTM0LTQ1YjNiM2VlM2QzOCJ9.AX6cazUoAiSafGi3l8oGgJje7I7S6DfAakcU3zFqdHJ2DVnVYGp0CFDIOP9IEzTx-z9jdTSPzcYcXrRqJT4sY3cKqcuLumF-i1GDyTiNmQtrGmfBdjAy5oGbMeR_ef9Xl_bF94SsI9nM6LIyA8LzW0PtcHfxoyUUefANnFHfxIsD45vpb4YG6mf48hMMvfuNYkbGX4ht7FjwcXl63y3s76l98AvE-sbG7nWZCHIVqqjr0RYJ2IjE65bIVAEAMTIi0o-254j2QyT35GhloLH_tBDU16LBhq5kmdZ7Fbu0e4uIc48I8UjOCe1fBd1EYin_UgP6ihB39tVpWKWSGTzHAQ"
}
```

### Description

The generated identity token is a JWT and it'll be required to continue the sign up process. The `success` property will be false when the validation failed (the validation code doesn't match the sign up id).