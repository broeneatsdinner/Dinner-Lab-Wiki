##### Variables
###### These are encapsulated by curly braces {} and are replaced with equivalent $.

Markdown | Less | Pretty
--- | --- | ---
*Still* | `renders` | **nicely**
1 | 2 | 3

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

Remember you will need to restart the app after changing the template.

## Public Files

All static files in Raneto (images, CSS, Javascript files etc.) are served from the `public` folder. This
is so that no one can access any other files in the install. Only files in the `public` folder are available
to the public.

It's worth noting that when customising Raneto you should always make your own files rather than customising
the existing Raneto files, so that your changes don't get lost when you
[update Raneto](%base_url%/updates/updating-raneto).

## Template Variables

Below are a list of template variables available to use in their respective templates:

**home.html**

* `config`: Holds an array of values from `config.js`
* `pages`: Structured list of categories and pages (used for navigation)
* `body_class`: Class for the `<body>` tag

**page.html**

* `config`: Holds an array of values from `config.js`
* `pages`: Structured list of categories and pages (used for navigation)
* `body_class`: Class for the `<body>` tag
* `meta`: Holds an array of values taken from the page meta comment block (e.g. `meta.title`)
* `content`: The HTML content of the page
* `last_modified`: The formatted date of the time the file was last modified

**search.html**

* `config`: Holds an array of values from `config.js`
* `pages`: Structured list of categories and pages (used for navigation)
* `body_class`: Class for the `<body>` tag
* `search`: The current search query
* `searchResults`: An array search results

## Array Structure

The `pages` array has a structure similar to the following:

* `slug`: The categoy slug
* `title`: The category title
* `is_index`: True for the top level files (ie not in a category)
* `class`: CSS class
* `sort`: The sort index for this category
* `files[]`: Array of pages in this category
	* `slug`: The page slug
	* `title`: The page title
	* `active`: True if the current page is "active"
	* `sort`: The sort index for this page

The `searchResults` array contains items which include:

* `slug`: The page slug
* `title`: The page title
* `body`: The page content
* `excerpt`: The page excerpt
