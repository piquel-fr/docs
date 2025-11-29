# Email system documentation

## Endpoints

### `GET /email` - List accounts

Available query parameters:
- `count`: Will return just the number of accounts
- `user`: The user to get the accounts for. If empty, will use the currently logged in user.

### `PUT /email` - Add email account

Account creation info should be specified in a JSON object in the body of the request payload.
The following fields are required:
- `email`: The email address of the account.
- `name`: The name of the account. This is for display purposes only
- `username`: The username of the mail account.
- `password`: The password of the mail account.

### `DELETE /email/{email}` - Delete email account

Will delete the specified email account.

### `GET /email/{email}` - Get account info

Returns a JSON object.

```ts
{
    email: string,
    name: string,
    mailboxex: []{
        name: string,
        num_messages: number,
        num_unread: number,
    },
}
