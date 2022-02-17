# Authentication

The Alert Logic Managed Web Application Firewall (WAF) Authentication page includes the following sections. Click on the link to go to the corresponding section to learn more:

<!--<MadCap:menuProxy mc-linked-toc="$topicHeadings" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />-->
To go to the documentation for the previous section of Alert Logic Managed Web Application Firewall (WAF), see [Output Filter](ref_services_policy_output_filter.md). To go to  the documentation for next section in the WAF section, see [Deny and Error Handling](ref_services_deny_and_error_handling.md).

**To access the Authentication section in the WAF management interface**:

1. On the left panel, under Services, click **Websites**.
2. On the Websites page, click the website you want to manage.
3. Under WAF, click **Policy**, and then scroll down to the Authentication section.

If you want to see all the settings on the Policy page, on the upper-right corner, change  the **Display preset** to **Advance**.

To save configuration changes or edits you make to any features and options, you must click **Save** on the lower-right of the section or page where you are making changes. Click **apply changes** on the upper-left corner of the page, and then click **OK**. Your changes will not be stored if you do not properly save your changes.

## SSL client authentication

<colgroup></colgroup>| **              Verify Client             ** Drop-down list | This directive enables the verification of the client identity. When set to deny all requests for the web application will be denied.<dl><dt>                Require              </dt><dd>Ask for the client certificate and only allow client access if a valid certificate is presented.</dd><dt>                Optional              </dt><dd>Ask for the client certificate and checks the client identity if the certificate is presented by the client.</dd></dl> |
| **              Verify Depth            ** Input field | Sets how deep WAF should go in the client provided certificate chain in order to verify the client identity.<dl><dt>                Valid input              </dt><dd>An integer in the interval 1 to 50.</dd><dt>                Default value              </dt><dd>10</dd></dl> |

##### Certificate Authority certificates

One or more Certificate Authority certificates are required for authenticating clients.

To upload an authority certificate click the **Add Certificate Authority certificate** button. This will expand an area in which you paste the certificate authority certificates. Be sure to include the -----BEGIN CERTIFICATE----- and -----END CERTIFICATE----- lines.

To view detailed certificate information click the + in the left column.

##### Certificate forwarding

The entire client certificate or specific certificate information can be forwarded to the backend web server in HTTP request headers.

The information selected will be forwarded in HTTP headers with the name of the selected info, ie. SSL_CLIENT_CERT will be forwarded in the header SSL_CLIENT_CERT.

<colgroup></colgroup>| **              Client Certificate Field            ** | <dl><dd>Select the cert field to match<dl><dt>                    SSL_CLIENT_SERIAL                  </dt><dd>The serial of the client certificate</dd><dt>                    SSL_CLIENT_S_DN                  </dt><dd>Subject DN in client's certificate</dd><dt>                    SSL_CLIENT_I_DN                  </dt><dd>Issuer DN of client's certificate</dd><dt>                    SSL_CIPHER                  </dt><dd>Cipher for established SSL-connection</dd><dt>                    SSL_CLIENT_CERT                  </dt><dd>PEM-encoded client certificate</dd><dt>                    SSL_CLIENT_VERIFY                  </dt><dd>Verification status - SUCCESS, FAILED or NONE if no cert granted by client</dd><dt>                    SSL_PROTOCOL                  </dt><dd>Protocol for the established SSL connection</dd><dt>                    SSL_SESSION_ID                  </dt><dd>SSL session ID for the established SSL connection</dd></dl></dd></dl> |
| **Description** |  |
| **Forward** Check box |  |

#### SSL client Certificate Revocation Lists (CRLs)                     

WAF uses Certificate Revocation Lists (CRL) to support certificate revocation.

To use CRL, configure a location where WAF can retrieve CRLs. When configured CRLs are downloaded and compiled at regular intervals to make sure that CRL updates are included.

Downloaded CRL files are displayed in the table below the CRL location rules.

<colgroup></colgroup>| **              Enable            ** Check box | Select to enable CRL checking for certificate. Default: <not selected> |
| **              CA Certificate            ** Drop-down list | Select the CA certificate to enable CRL checking for. |
| **              Location URL            ** Input field | A URL that points to the directory the where the CRL files are served from or directly to a CRL-file if CRLs for the CA are served as one (big) file.<dl><dt>                Valid input              </dt><dd>A URL</dd><dt>                Input example              </dt><dd>http://crl.eid.belgium.be/ - the CRL repository for the Belgian eID.</dd><dt>                Default value              </dt><dd>none</dd></dl> |
| **              Type            ** Drop-down list | The type of the Location URL - index or file.<dl><dt>                Index              </dt><dd>The URL Location points to a directory that contains a number of CRLs that has to be downloaded.</dd><dt>                CRL File              </dt><dd>The URL Location points directly to a single file that contains all CRLs for the CA.</dd></dl> |
| **              Wildcard            ** Input field | If the URL Location type is Index it is necessary to specify a wildcard that matches the CRL files in the location.<dl><dt>                Valid input              </dt><dd>A simple wildcard.
Use the following characters to specify wildcards:
`* =` any string any length.
`? =` one occurrence of any character.</dd><dt>                Input example              </dt><dd>*.crl - matches all files with extension .crl</dd><dt>                Default value              </dt><dd>*</dd></dl> |
| **              Test            ** Button | Before saving the CRL rule click the Test button. This will display all CRL files in the location matching the CRL location rule. |

#### SSL client authorization                     

In addition to generally restricting access to the website based on validity of client certificate it is possible to specify requirements which has to be fulfilled in order to allow access to website resources defined as paths.

Suppose you have an organisation, Snake Oil, that have a website to which they only want employees with valid client certificates issued by Snake Oil to be able to access in general. In the website there is an area, /management/, that they only want management to be able to access.

The first requirement can be achieved by requiring a valid Snake Oil certificate to access the website.

The second requirement can be met by creating an authorization rule that matches the Organisational Unit of the Subject DN, like: Location=/management, SSL_CLIENT_S_DN regex match OU=management.

<colgroup></colgroup>| **              Location            ** | In the list enter one or more regular expressions defining locations. Note that the expressions are matching left to right so the expression can be a simple path like `/management` which match any path in the website tree starting with /management but not /employees/management.<dl><dt>                Valid input              </dt><dd>A valid regular expressions</dd><dt>                Input example              </dt><dd>/admin (any request starting with "/admin")
/management (any request starting with "/management")
.+\.php (any request for files with the extension ".php")</dd><dt>                Default value              </dt><dd>`none`</dd></dl> |
| **              Requirements            ** | One or more requirements to be met for the client to be allowed access to the specified location. Using the operators AND and OR complex requirements can be specified. The AND operator precedes the OR operator so O=Snake Oil AND OU=management OR O=Rattle Snake Oil AND OU=admin will be evaluated as (O=Snake Oil AND OU=management) OR (O=Rattle Snake Oil AND OU=admin).<dl><dt>                Client cert field              </dt><dd>Select the cert field to match<dl><dt>                    SSL_CLIENT_SERIAL                  </dt><dd>The serial of the client certificate</dd><dt>                    SSL_CLIENT_S_DN                  </dt><dd>Subject DN in client's certificate</dd><dt>                    SSL_CLIENT_I_DN                  </dt><dd>Issuer DN of client's certificate</dd><dt>                    SSL_CIPHER                  </dt><dd>Cipher for established SSL-connection</dd><dt>                    SSL_CLIENT_CERT                  </dt><dd>PEM-encoded client certificate</dd><dt>                    SSL_CLIENT_VERIFY                  </dt><dd>Verification status - SUCCESS, FAILED or NONE if no cert granted by client</dd><dt>                    SSL_PROTOCOL                  </dt><dd>Protocol for the established SSL connection</dd><dt>                    SSL_SESSION_ID                  </dt><dd>SSL session ID for the established SSL connection</dd></dl></dd><dt>                Match type              </dt><dd>Select `Regex Match` to require a match or `Regex No Match` to negate match.</dd><dt>                Match criteria              </dt><dd>A regular expression to match data in the client cert field selected.
Example: If SSL_CLIENT_S_DN is selected `OU=management` would match certificates where the client cert has Organisational Unit = management.</dd></dl> |
