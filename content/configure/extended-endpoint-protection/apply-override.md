# Apply an Override

Alert Logic Extended Endpoint Protection uses a combination of machine-learning attribute analysis and dynamic behavior analysis to identify and block malware. If Alert Logic blocks a program that you want to approve, you can apply an override. Overrides prevent a protection indicator from blocking a specific file path or file hash.

## Manage overrides

When you create an override, you add an exception to the protection logic. This exception operates on either the file path or the file hash level, which depends on when Alert Logic blocked the program. Creating an override allows flexibility when needed without compromising your protection.

To create an override:

1. In the Alert Logic console, click the ![](../../Resources/Images/dashboard/configure-icon.png)**Configure** menu item, click **Endpoints**, and then click the **Events** tab.
2. Select the event grouping in the list, and then click **Override**.
3. A check mark icon appears next to the incident grouping, indicating that  no more incidents will appear on any endpoint that checks into the portal.

To remove an override:

1. In the Alert Logic console, click the ![](../../Resources/Images/dashboard/configure-icon.png)**Configure** menu item, click **Endpoints**, and then click the **Events** tab.
2. Select the override you want to remove in the list, and then click **Edit**.
3. Click **Remove Override(s)**.
