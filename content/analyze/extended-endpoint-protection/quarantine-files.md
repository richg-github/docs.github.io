# Quarantine and Delete Files

In addition to automatically stopping malicious processes, Extended Endpoint Protection can quarantine malicious executables on the endpoint. Quarantining moves the file to a quarantine location on the device and encrypts the file so that end users cannot make further attempt to access and execute it. You can manually quarantine files related to an event or enable automatic quarantine to enable Extended Endpoint Protection to automatically place files in quarantine. Administrators can view quarantined files in the portal and either release them from quarantine by applying an event override or permanently delete them.

## Manually Quarantine a File

You can manually quarantine a file for any events blocked by Extended Endpoint Protection.

To manually quarantine a file, go to the [Event Detail](../../configure/extended-endpoint-protection/manage-endpoints.md) page and select **Quarantine**. A pop-up box confirms that you want to add all the events in the group to quarantine. Once quarantined, files will appear in a table within the modal, and you will have the option to permanently delete them.

## Enable Automatic Quarantine

The Extended Endpoint Protection auto-quarantine feature is disabled by default. To enable auto-quarantine, go to the Protection page under Settings and slide the toggle to enable Automatic Quarantine, and save changes.

When auto-quarantine is enabled, Extended Endpoint Protectionwill mark files with the Malicious EXE Launched indicator and move them to a quarantine location on the endpoint, and then encrypt these files so they cannot be executed while in quarantine.

Note that auto-quarantine will only work on devices where protection is ON.

View &amp; Manage Quarantined Files

View Quarantined Files

You can view quarantined files from the Event Detail page for an event group. To browse to the Event Detail page, go to Events and then click into any event group. If an event group contains quarantined files, the event summary information will indicate the number of files quarantined for that group. You can view the quarantined files by clicking Quarantine at the top of the event group.

Restore Quarantined Files

To restore quarantined files associated with an event group, simply Apply an Override for that event. Overriding the event will release the quarantined files and ensure that Extended Endpoint Protectiondoes not block or quarantine future instances of that event. We recommend that you only apply overrides for programs you recognize and trust.

Delete Quarantined Files

To permanently delete files from quarantine, browse to the Quarantine modal from the Event Detail page. Select the files from quarantine that you wish to delete then click Delete and confirm deletion. Deleting files is a permanent action that removes files from the endpoint. We recommend that you only delete programs you have reviewed and confirmed to be malicious.
