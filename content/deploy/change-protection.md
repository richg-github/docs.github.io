# Change Protection Level of an Asset

When you create a deployment, Alert Logic prompts you to assign the scope of protection for each  asset included in the deployment. Your [subscription](../get-started/subscriptions-addons.md) determines the level of protection you can assign to the assets. You can change protection levels as your needs or [entitlements](../analyze/reports/service/entitlement/entitlement-summary.md) change.

Alert Logic discovers and organizes deployments into a visual topology where you can select the desired levels of protection for your assets. You can define the scope of protection per network, VPC, VNET,  or region. Each node appears within its protected region.

For Data Center deployments, you can also define the scope of protection per subnet.

To change the protection level of an asset:

1. In the Alert Logic console, click the menu icon (![](../Resources/Images/dashboard/menu-icon.png)) to see the navigation menu.
2. Click **Configuration**, and then click **Deployments**.
3. Find the deployment you want to edit, and then click **EDIT**.
4. In the left navigation panel, click **Scope of Protection**.
5. In the visual topology, click the region or individual node you want to change, and then select the coverage level:
   * Unprotected
   * Essentials
   * Professional
   * Enterprise
7. Click **SAVE**.

**About the Scope of Protection choices:**

The choices available for scope of protection correspond directly with your entitlement. Although a Professional subscription includes all the features of Essentials, a Professional customer cannot set the protection scope to Essentials unless the account has a separate Essentials subscription. Likewise, an Enterprise customer cannot set the protection scope to Essentials or Professional unless the account has separate subscriptions for those.
