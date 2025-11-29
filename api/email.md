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

Returns a JSON object that complies with the follow type:
```ts
interface MailAccount {
  email: string;
  name: string;
  mailboxes: {
    name: string;
    num_messages: number;
    num_unread: number;
  }[];
}
```

For example:
```json
{
  "email": "user@example.com",
  "name": "Jane Doe",
  "mailboxes": [
    {
      "name": "Inbox",
      "num_messages": 42,
      "num_unread": 5
    },
    {
      "name": "Spam",
      "num_messages": 12,
      "num_unread": 0
    }
  ]
}
```
