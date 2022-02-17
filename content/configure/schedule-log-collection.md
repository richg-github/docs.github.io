# Log Management Collection Schedules

When you create a Log Management policy for the first time, you can create collection schedules. Collection schedules allow you to black out periods when you do not need to collect log sources. You can create new collection schedules for a policy at any time. However, you cannot delete or update existing schedules.

For more information about policy creation, see [Log Management Policies](log-management-policies.md).

To access the Log Management collection schedules, click ![](../Resources/Images/dashboard/configure-icon.png)**Configure**, click **Log Management**, and then click **Policies**. Click the corresponding policy tab to  find the policy for the schedule you want to create.

## Create a collection schedule

To create a collection schedule:

1. In the Alert Logic console, click the menu icon (![](../Resources/Images/dashboard/menu-icon.png)).
2. Click ![](../Resources/Images/dashboard/configure-icon.png)**Configure**, click **Log Management**, and then click **Policies**.
3. On the Policies page, click the corresponding tab to find the policy for the schedule you want to create.
4. In the list of policies, click the pencil icon (![](../Resources/Images/pencil icon.png)) for the policy you want to create a schedule.
5. In **Collection Schedule Blackout Periods**, select **Create a new schedule**.
6. In **Schedule Name**, type a descriptive name .
7. Select a **Schedule Time Zone**, and then select **Blackout Periods** to enable blackout periods. Also, you can add or remove extra blackout periods.
8. Click **SAVE**.

## Update a collection schedule

If you update, archive, or delete any collection, policies, or alert rule configurations, you could break interconnected configurations.

To update a collection schedule:

1. Browse to the **Policies** page.
2. Click the corresponding policy tab.
3. In the list of policies, click the pencil icon (![](../Resources/Images/pencil icon.png)) for the policy you want to create a schedule.
4. In **Schedule Name**, type a descriptive name.
5. Select a schedule time zone.
6. Select **Blackout Periods** to enable blackout periods. You can add or remove extra blackout periods.
7. Click **Update**.

## Delete a collection schedule

If you update, archive, or delete any collection, policies, or alert rule configurations, you could break interconnected configurations.

To delete a collection schedule:

1. Browse to the **Policies** page.
2. Click the corresponding policy tab.
3. In the list of policies, click the he trash icon (![](../Resources/Images/Icons/trash icon.png) ) for the collection schedule you want to delete, and then click **Delete**.
