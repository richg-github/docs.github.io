# Certificates and Keys

If you have an Alert Logic MDR Professional  or an Alert Logic MDR Enterprise subscription and administrative privileges to manage certificate and keys, you can upload certificates.

Access the Alert Logic Certificates and Keys page in the Alert Logic console. Click the ![](../Resources/Images/dashboard/configure-icon.png)**Configure** menu item, and then click **Certificates and Keys**.

## Manage security certificates

### Upload security certificates

Customers with administrative privileges can upload security certificates in the Alert Logic console.

After you upload your certificate, the Alert Logic provisioning team performs a back-end installation to validate your certificate.

To upload security certificates:

1. In the **Certificates and Keys** page, click the add icon (![](../Resources/Images/Icons/cdAddPlus.png)).
2. In the slideout panel, complete the required fields:
   * **Name**- Type a unique name to identify the certificate.
   * **Certificate Content**—The PEM-encoded certificate. This field must  include the header and footer notes.
   * **Private Key Content**—The PEM-encoded private key. This field must include the header and footer notes. The PEM-encoded private key must be in RSA format, or you must convert the key to RSA format.
                           You cannot change the certificate name after you enter and save it.      

1. The correct format for the **Certificate Content** field:

The public certificate is the section of the certificate file between (and including) the certificate start and end tags.
<kbd>-----BEGIN CERTIFICATE-----</kbd>
<kbd>Certificate characters</kbd>
<kbd>-----END CERTIFICATE-----</kbd>
1. The correct format for the **Private Key Content** field:

The private key is the section of the certificate file between (and including) the private key start and end tags.
<kbd>-----BEGIN RSA PRIVATE KEY-----</kbd>
<kbd>Private key characters</kbd>
<kbd>-----END RSA PRIVATE KEY-----</kbd>
1. Click **Save**.

You can upload a PEM file instead of completing the empty fields.

**To upload a PEM file**:

1. Click  **PEM File Upload** field, and then search for and select the desired PEM file.

Your PEM file must have both certificate information and private key information.
1. Click **Save**.

Allow about 15 minutes for your system to update with these changes. Once uploaded, your certificate is listed in the **Certificates and Keys** page.

### View security certificates

Customers with administrative privileges   in the Alert Logic console can view information for public certificates. Alert Logic protects confidential private keys, so you cannot retrieve or view private keys.

To view information about a certificate, in the **Certificates and Keys** page, in the list of certificates, click anywhere on the row of the certificate you want to see. A slideout panel, which includes the name of the certificate and the certificate contents appears on the right side of the page.

### Delete security certificates

Customers with administrative privileges  can delete security certificates in the Alert Logic console.

When you delete a certificate, you permanently remove it.

To delete security certificates:

1. In the **Certificates and Keys** page, in the certificates list, to the right of the certificate you want to remove, click the delete icon (![](../Resources/Images/Icons/trash icon.png)).
2. Click **DELETE** in the slideout panel.
