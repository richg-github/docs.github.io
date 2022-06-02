---
title: "Accounts and User Types"
date: 2018-12-29T11:02:05+06:00
weight: 3
draft: false
---

You can access Alert Logic APIs as a user associated with a specific account. When Alert Logic APIs pulls account information, you cannot switch accounts during a process. Users belong to a single account, and though you may have an account that manages other accounts, you must choose one account each time you work with the APIs. Multi-account users must be careful and deliberate when working in the API to ensure that the intended account is selected.

### Types of user roles

User roles available in the Alert Logic console include the following:

* Administrator—The Administrator role allows full management of, and read access for, the account and any managed accounts. Only administrators can create and manage other users for the managing account and for managed accounts. Administrators can also control features for the managing account and all its managed accounts.

* Owner—The Owner role allows full management and read access for the user account they are assigned, but do not have the ability to edit other user accounts. Owners also have full read and modify permissions to any managed accounts, including the ability to edit users on the managed accounts. Owner accounts cannot create or delete users in managed accounts.

* Power User—The Power User role allows full access within the managing account, except for user management. Power users can view all the information in their managed accounts, but cannot modify the information (including user accounts).

* Support/Care—The Support/Care role allows only read access for the managing account and all its managed accounts.

* Read Only—The Read Only role allows only read access for the managing account. Users assigned this role cannot make changes and cannot view information for any managed accounts.

### Service users

Alert Logic recommends creating a dedicated user for automation efforts. A service user prevents password lockout when staff changes and keeps everything in one dedicated place.

To create a service user:

1. Set up a new user in the Alert Logic console using a valid email address.
2. Choose the user role based on your needs.
3. Use an access key and secret key instead of a password.

For more information, see Customer Accounts, User Accounts, and User Roles.