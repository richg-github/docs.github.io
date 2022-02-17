# Learning

Learning is a section  in the Alert Logic Managed Web Application Firewall (WAF) management interface. To access the Learning  section, click **Websites** on the left panel, under Services. On the Websites page, click the website you want to manage, and click **Learning status** to access the first section.

Learning includes the following features. Click on the link to go to the corresponding documentation to learn more:

* [Learning](#)
   * [Learning status](#ref_services_learning_status.md)
   * [Learning Data](ref_services_learning_data.md)
   * [Alert Logic Managed Web Application Firewall (WAF) ](ref_services_response_data.md)
   * [Learning Settings](ref_services_learning_settings.md)

This document includes the following sections. Click on the link to go to the corresponding section to learn more:

<!--<MadCap:menuProxy mc-linked-toc="$topicHeadings" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />-->
To go to the documentation for the previous section of Alert Logic Managed Web Application Firewall (WAF) management integration, see [Deny and Error Handling](ref_services_deny_and_error_handling.md). To go to  the documentation for next subsection in the Learning section, see [Learning Data](ref_services_learning_data.md).

To save configuration changes or edits you make to any features and options, you must click **Save** on the lower-right of the section or page where you are making changes. Click **apply changes** on the upper-left corner of the page, and then click **OK**. Your changes will not be stored if you do not properly save your changes.

The Learner builds a complete profile of the web site including static requests, web applications and input parameters bu analyzing incoming requests.

To avoid learning from worms, attacks and other unauthorized access the Learner employs a combination of heuristic attack classification, statistics and server responses.

When learning is enabled for the website the Learner keeps analyzing requests until no changes to the resulting policy are recorded. That is, for every 10,000 requests the Learner builds a trial policy, compares it to the former trial policy and records the number of changes. When a configurable number of trial policies in a row (default 30) has not resulted in a number of changes between each trial build exceeding a configurable threshold (default 0) a policy is built.

By default the Learner is configured to generate a short yet fine grained policy. This is achieved by identifying global characteristics of the web site and generating global patterns matching those characteristics. The global patterns typically account for the majority of the web systems content and applications leaving only the "real" web applications to be accounted for by specific web application policy entries.

## Learning status

### Learning progress indicators

The two bars in the top of the page indicates the current state of sampling and verification.

The Learner works in two stages when profiling the website.

1. **Sampling progress**
This is the process of collecting information about the website in terms of what paths/applications are used, what parameters do they take as input, what extensions are used for static content, etc.
2. **Verification**
The verification process 1) validates the data samples using statistical methods like analyzing spread in IP sources and time, number of requests, etc. and 2) verifies that the resulting policy covers the requests sampled.
As the Alert Logic Managed Web Application Firewall (WAF) Learner extracts characteristics like extensions, specific directories in paths and global parameters (parameter names a number of applications take as input - like print=1) and even patterns used in global parameters the verification process may start before the Data sampling progress has reached 100%.
Verification is calculated as the number of sample runs in a row with no policy changes relative to the required number configured in learner settings.
When Verification has reached 100% WAF will either build and commit a new policy or notify the administrator by email that verification has reached 100% and a new policy can be built and committed.

### Policy resulting from current learn settings

This section shows a sample of the policy resulting from the *Learner* settings effective.

When the settings are changed the resulting policy sample is rebuilt using the new threshold values. This is done as a background job and depending on the load on the WAF node and the complexity of the sample data it may take anywhere from e few seconds to a minute or two to build the policy. If the new policy is not visible yet, wait a while and refresh the window.

<table>
  <colgroup>
    <col></col>
    <col></col>
  </colgroup>
  <tbody>
    <tr>
      <td>
        <b>              Commit to WAF            </b>
        <p>Button</p>
      </td>
      <td>
        <p>Builds a policy which is accessible and editable in the Global Patterns and Web applications windows.</p>
        <p>When clicked the policy displayed in the table will be committed to the WAF engine, that is: made active for filtering requests.</p>
        <p>If policy verification has not reached a warning message (two actually) will be displayed asking to confirm the action. Remember: Alert Logic Managed Web Application Firewall (WAF) is a white-list based WAF. If the policy put into production does not match real life requests building the policy prematurely (not fully verified) is likely to result in false positives. If verification has not reached 100% it means that it not verified that the policy does not generate false posivites. Have patience and wait for verification to reach 100%.                           </p>
      </td>
    </tr>
    <tr>
      <td>
        <b>              Web applications            </b>
        <p>Expandable: Click <b>+</b> to expand.                           </p>
      </td>
      <td>
        <p>Learned web applications.</p>
        <p>Expand the item to get a list of applications learned. For each application is shown:</p>
        <ul>
          <li>
            <p>URL path</p>
          </li>
          <li>
            <p>Methods learned</p>
          </li>
          <li>
            <p>Parameters.</p>
            <p>Parameters are shown as name, value pairs where the value is the name of the input validation class learned for that parameter.</p>
            <p>Note that only the applications private parameters are shown here. Parameters which the application have in common with other applications are included in the Global parameters list.                                    </p>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>
        <b>              Global URL patterns            </b>
        <p>Expandable: Click <b>+</b> to expand.                           </p>
      </td>
      <td>
        <p>Global URL Path Policy built from learned applications.</p>
        <p>For each application group (see <a href="ref_services_learning_data.md#ref_services_learning_data.md#ref_services_learning_data_applications_learned">Applications learned</a>) a regular expression is built which matches all samples in that specific group.                           </p>
        <p>Most CMS based web systems have a number of global parameters, like for instance <code>print=1</code>, which can be appended to most requests. Without the combination of <em>Global URL Path Policy</em> and <em>Global Parameters Policy</em> pages with static content that take global parameters, like <code>index.php?print=1</code>, would be learned as web applications and the URL paths would have to be added to the policy as web applications. This can potentially result in a huge policy which is never up to date because new content is added all the time.                           </p>
        <p>By making global policies that account for all the static content which is served dynamically only "real" web applications with a number of private parameters have to be mapped in detail.                            </p>
        <p>Thus the global patterns allows for building a condensed, yet fine grained, policy which also account for future standard content added to the web site.                            </p>
      </td>
    </tr>
    <tr>
      <td>
        <b>              Global parameters            </b>
        <p>Expandable: Click <b>+</b> to expand.                           </p>
      </td>
      <td>
        <p>Global Parameters Policy built from learned applications.</p>
        <p>Displayed in the format:</p>
        <p>
          <code>name = value</code>
        </p>
        <p>Depending on the Name grouping threshold value the name can either be a literal string or a regular expression matching a number of parameter names with name and value similarities.                            </p>
        <p>The value is displayed as a class name. When the policy is built the corresponding regular expression will be used.</p>
      </td>
    </tr>
    <tr>
      <td>
        <b>              Static content allowed extensions            </b>
        <p>Expandable: Click <b>+</b> to expand.                           </p>
      </td>
      <td>
        <p>Learned static path extensions which will be allowed. </p>
      </td>
    </tr>
    <tr>
      <td>
        <b>              Static content path allowed characters            </b>
        <p>Expandable: Click <b>+</b> to expand.                           </p>
      </td>
      <td>
        <p>Unique characters and character classes (like 'A' - all international word characters) learned from static path samples.</p>
        <p>Also the regular expression built to match requests for static content is shown. Note the last set of parantheses preceded by an escaped period <code>\.(\w+)</code>. This part will be matched with the list of allowed extensions to determine if the extension is alowed.                           </p>
      </td>
    </tr>
  </tbody>
</table>### Policy history

When a new policy is generated and committed, either automatically or manually, it is added to the Policy history list.

<colgroup></colgroup>| **              Policy history            ** | The policy number. |
| **              Type            ** | Automatic or manual (requested by administrator user) |
| **              Report            ** | Click link to see resulting policy and changes compared to the former (if any). |
| **              Sample run            ** | The sample run number at which the policy was generated. |
| **              Web Apps            ** | The number of entries in the `Web Application Policy`. |
| **              Global URLs            ** | The number of entries in the `Global URL Policy`. |
| **              Global Parms            ** | The number of entries in `Global Parameter Policy`. |
| **              Static            ** | The number of entries in static file types `Static Content Policy`. |
| **Time** |  |

### Sample run information

The Learner analyzes request samples in chunks of approximately 10,000 requests (or more if the system is very busy) . For each sample run an entry is added to the Sample run information table which shows total and delta values of summarizing the learning process.

<colgroup></colgroup>| **              Sample run            ** | The sample run number. |
| **              Hits total            ** | The total number of hits processed during the learning process. |
| **              URL paths            ** | Total number of unique URL paths identified. |
| **              Parameters            ** | Total number of unique parameter names identified. Uniqueness is determined by URL path. Two parameters with the same name but mapped as belonging to different URL paths are therefore identified as two unique parameters. When the policy is built WAF identifies parameters with similar names and input data as as global in scope and builds global patterns matching such parameters. |
| **              Changes            ** | When the chunk of raw sample data has been processed WAF builds a policy based on the total sample population. This policy is compared to the policy built in the last sample run and changes are recorded. The number shown is the sum changes recorded to the Web Application Policy (`ACL`), Global URL Policy (`GURL)`, Global Parameter Policy (`GParm`) and the Static Content Policy (`EXT`). Click on the number shown to get a change report detailing the changes. |
| **              ACL            ** | The number of changes to the `Web Application Policy` compared to the sample run before. |
| **              GURL            ** | The number of changes to the `Global URL Policy` compared to the sample run before. |
| **              GParm            ** | The number of changes to `Global Parameter Policy` compared to the sample run before. |
| **              Ext            ** | The number of changes to the `Static Content Policy` compared to the sample run before. |
| **Updated time** |  |

The number of policy changes recorded is calculated with the *Learner* settings effective when the sample data is analyzed. Whereas the resulting policy (below) is recalculated when the *Learner* settings are changed this is not the case with the sample run policy builds. It is therefore possible that the two sections show different results. The next sample run is run using the new settings.

### Lower button bar

The lower button bar contains the following buttons.

<colgroup></colgroup>| **              Re-analyze data            ** Button | To see the effect of deleting selected learning data in the resulting policy section click this button. Wait a few seconds and reload the page. |
| **              Reset learn data            ** Button | Use with caution! When clicking this button and accepting the confirm pop-up window. *All learning data for that proxy will be deleted!* If learning is enabled the learning and data sampling process will start from scratch. |
