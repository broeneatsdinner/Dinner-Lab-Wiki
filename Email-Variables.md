##### Variables

These are encapsulated by curly braces {} and are replaced with equivalent $.

| Email Variable | PHP Variable | Notes |
| ------ | ------ | ------ |
| `{cityID}`           | `$cityID` | |
| `{cityDisplayName}`  | `$cityDisplayName` | |
| `{referrerKickback}` | `$referrerKickback` | |
| `{trialDuration}`    | `$trialDuration` | |
| `{credits}`          | `$credits` | |
| `{amount}`           | `$amount` | Amount the user was charged in USD (IF they had a promo with a non-NULL amount), without the $ sign (strictly numbers + decimals if applicable) |
| `{usertypeID}`       | `$usertypeID` | |
| `{usertype}`         | `$usertype` | The english-language equivalent of usertypeID, for instance, FREE MEMBER (and yes, it's all caps in the DB) |
| `{firstname}`        | `$firstname` | |
| `{lastname}`         | `$lastname` | |
| `{fullname}`         | `$fullname` | |
| `{email}`            | `$email` | |
| `{password}`         | `$password` | This will never be the user's password in plaintext, but rather, their temporary password that is generated for them by a Superadmin. |
| `{URL}`              | `$URL` | |
| `{inviteURL}`        | `$inviteURL` | |
| `{submitMenuURL}`    | `$submitMenuURL` | |
| `{code}`             | `$code` | |
| `{message}`          | `$message` | |

There may be additions since this was written.