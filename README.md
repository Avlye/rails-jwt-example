# Ruby on Rails API + JWT Authentication Example

A Simple Reference for learning how to implement a basic Ruby on Rails API with JWT Authentication.

# UsersControllers

UserControllers provides the JWT authorization controller.

```ruby
before action => check authorization on auto_login
```

## Encode Payload with s3cr3t

_WARN: Don't use hardcoded secrets on production!_

Makes a request via _{ Authorization: 'Bearer <token>' }_
and start decoding JWT and also verify validation.

```
=> If could not decode, in this case it returns nil

=> Once you decoded, find the user id into database
```

<!-- prettier-ignore-start -->
## Register:

**NOTE:** This is only a pseudo-code
```ruby
POST => {
  Authorization: 'Bearer <token>',
  username: string,
  password: string,
  age: number
}

Checks validations
  => Encode token session and send { @user, token: JWT::Payload }
  => ELSE:
    => Returns `Invalid username or password `
```

## Login:
```ruby
POST => {
  Authorization: 'Bearer <token>',
  username: string,
  password: string
}

Find the user in database,
IF user exists
  => authenticate as:
      (password: string => BCryptHash) == (password_digest: BCryptHash).

  => Returns { @user, token: JWT::Payload }
```
<!-- prettier-ignore-end -->
