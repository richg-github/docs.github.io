# Manage Your SSL Certificates

When you create an SSL website, Alert Logic Managed Web Application Firewall (WAF) gives this website a temporary SSL certificate. You are able to substitute the temporary certificate with a signed certificate. These actions are only intended for SSL enabled website proxies. To create an SSL website, see [Add a website](configure.md#addWebiste). For more information about configuring a website, see [Configure Alert Logic Managed Web Application Firewall (WAF)](configure.md).

## Export an SSL certificate

When you create a website proxy for an existing HTTPS web server, you need to export the SSL certificate from the web server, and import the certificate to WAF.

WAF supports the imports of  the following formats:

* PKCS12 (or PFX): The standard format used by Microsoft IIS servers. It stores public key, private key, and the key chain in one single encrypted file.
* PEM: Commonly used in *nix based web servers like Apache and Nginx. When ordering certificates, this format is often referred to as “Apache format.”
* Intermediate: A subordinate certificate where the chain begins at the trusted root, through the intermediate and ending with the SSL certificate issued to you.

The links below open procedures that refer to third party products and guidelines and may change at the vendors discretion.

The following options show you how to export an SSL certificate from the most common servers:

## Export an SSL certificate from a Microsoft IIS server

When you export an SSL certificate from a Microsoft IIS server, the certificate is usually obtained in PKCS12 (<kbd>.pfx</kbd>) format. The instructions for exporting from IIS 7 below will include the SSL certificate chain.

### Add the certificate                

1. Open the **Windows Start** menu. In the **Search** box, type MMC and click **OK**.
2. Click the **File** tab and then select **Add/Remove Snap-in**.
3. Click on **Certificates**, and then click **Add**.
4. Select **Computer Account**, and then click **Next**. Select **Local Computer** and click **Finish**.
5. Select **Local Computer**, and click **Finish**.
6. Click **OK** to close the **Add/Remove **snap**-in** window.
7. In the center pane, double-click **Certificates (Local Computer)** in the center window.

### Export the certificate                

1. Double-click on the **Personal** folder, and then click **Certificates**.
2. Right-click the certificate you want would like to backup, and then select **ALL TASKS** and then **Export**.
3. Follow the Certificate Export Wizard to backup your certificate to a .pfx file.
4. Select **Yes, export the private key**.
5. Select **Include all certificates in certificate path if possible**.(do NOT select the **delete Private Key** option).
6. Type a password you will remember, and then save the file.
7. Click **Finish**. You will receive the following message, "The export was successful."
8. Click **OK**.

## Export an SSL certificate from an Apache server

For Apache-based web and application servers with default PEM encoding,  the SSL certificate can be copied directly from the file system and imported “as is” when the default PEM encoding is used.

Obtain the SSL-certificate file from the web servers file system. By default, the file is PEM-encoded.

The exact location may vary, but the Apache config file (<kbd>httpd.conf</kbd>) will show the exact location as in the example below:

<kbd>&amp;lt;VirtualHost 192.168.0.1:443&amp;gt;</kbd>

<kbd>DocumentRoot /var/www/html2</kbd>

<kbd>ServerName www.yourdomain.com</kbd>

<kbd>SSLEngine on</kbd>

<kbd>SSLCertificateFile /path/to/your_domain_name.crt SSLCertificateKeyFile</kbd>

<kbd>&amp;gt;/path/to/your_private.key</kbd>

<kbd>SSLCertificateChainFile /path/to/CA_chain.crt</kbd>

<kbd>&amp;lt;/VirtualHost&amp;gt;</kbd>

**Where:**

<kbd>SSLCertificateFile</kbd> is the server public key.

<kbd>SSLCertificateKeyFile</kbd> is the server private key.

<kbd>SSLCertificateChainFile</kbd> is the certificate chain.

Keep the contents of the files open. You will need it for the PEM (Apache) certificate upload section.

## Upload an SSL certificate

When you create an SSL website, WAF assigns the website a temporary SSL certificate. You are able to substitute the temporary certificate with a signed certificate.

**To replace the temporary certificate:**

1. In the main menu in the Alert Logic console, under ![](../../Resources/Images/dashboard/configure-icon.png)**Configure**, click WAF.
2. Click **Appliances**.
3. In the item row of your appliance, click **Manage Appliance**.
4. On the Manage Appliance page, in the left navigation pane, under **Services**, click **Websites**.
5. On the Websites page, select the website you want to view.
6. In the main menu, highlight **ADC**, and click **Virtual Host**.
7. Click **Manage Certificates**. The  SSL certificate currently in use is displayed. To upload a new certificate, click **Manage certificates.**

## PKCS12 (Microsoft IIS) certificate upload

1. In the Options list, select **Import SSL certificate (PKCS12 format)**.

![](../../Resources/Images/wsm/AWSCertificateFormat.png)3. Click **Choose File** to browse your system for the file location.
4. In **Passphrase input**, type the passphrase.
5. Leave **Validate certificate chain** selected.
      When checked, WAF validates that the certificate chain is complete and ordered correctly. This option should only be cleared if the certificate import is generating certificate chain errors that need to be adjusted manually after import.      7. Click **Save Settings** in the lower right corner of the page.
8. Click **Apply Settings** at the top of the page to apply the certificate to the run-time configuration.

## PEM (Apache) certificate upload

1. In the SSL certificate section, click **Manage certificates**.
2. Select **Import SSL certificate (PEM format)**. 
![](../../Resources/Images/wsm/AWSCertificateFormatPEMFile.png)
3. Open the .PEM file(s) in a text-editor. When obtained from the web server, the following extension convention is usually used:

<kbd>*.crt</kbd> – public keys, both server and CA chain

<kbd>*.key</kbd> – the private key

1. Copy the public certificate section of the certificate into the **SSL public key/certificate** field.

The public certificate is the section of the certificate file between (and including) the certificate start and end tags.

<kbd>-----BEGIN CERTIFICATE-----</kbd>

<kbd>Certificate characters</kbd>

<kbd>-----END CERTIFICATE-----</kbd>

1. Copy the (SSL) private key section of the certificate into the **SSL private key** field.

The (SSL) private key is the section of the certificate file between (and including) the private key start and end tags.

<kbd>-----BEGIN RSA PRIVATE KEY-----</kbd>

<kbd>Private key characters</kbd>

<kbd>-----END RSA PRIVATE KEY-----</kbd>

1. In the **Passphrase**, field type the passphrase for the private key  (if the original private key was encrypted).
2. Leave **Validate certificate chain** selected.        When checked, WAF validates that the certificate chain is complete and ordered correctly. This option should only be cleared if the certificate import is generating certificate chain errors that need to be adjusted manually after import.
3. Click **Save Settings** in the lower right corner of the page.
4. Click **Apply Settings** at the top of the page to apply the certificate to the run-time configuration.

1. (Optional) In **SSL authority certificate(s) chain**, if a certificate authority chain is provided with your certificate, enter the entire list of certificates (more than one certificate may be provided).

1. Click **Save settings**. The imported certificate is displayed in the certificate table along with the certificate chain (if any). Verify that the certificate is imported correctly.
2. Click the **Apply settings**.

 ## Intermediate certificate upload

1. In the SSL certificate section, click **Manage certificates**.
2. Select **Edit Certificate Chain**. 
![](../../Resources/Images/wsm/AWSEditCertificateChain.png)
3. Open the intermediate certificate in a text-editor. When obtained from the web server, the following extension convention is usually used:
The public key/certificate is the section of the certificate file between (and including) the certificate start and end tags.
<kbd>&amp;lt;-----BEGIN CERTIFICATE---&amp;gt;</kbd>
<kbd>Certificate characters</kbd>
<kbd>&amp;lt;-----END CERTIFICATE---&amp;gt;</kbd>
4. Click **Save Settings** in the lower right corner of the page.
5. Click **Apply Settings** at the top of the page to apply the certificate to the run-time configuration.
