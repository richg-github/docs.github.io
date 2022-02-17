# Online release notes template

This sample shows service pack release notes, but all categories should follow this format.

### Release date: February 22, 2018 (UK); March 1, 2018 (US)

#### Bug fixes

* This release fixes an issue where automatically closed disputes had the incorrect status of "Pending Review". This was corrected and now automatically closed disputes have the status "Finished Failing".
* This release fixes an issue where comments in the Overview page of Scan Dispute showed the customer name instead of the user name. The was corrected and the comments now show the user name instead of the customer name.
* This release fixes an issue where the PCI Executive Summary Report listed the scope twice, with one having incorrect status. This was fixed - the scope only lists once, with the correct status.
* This release corrects text on the Schedule PCI Scan page. "Hostnames must have no URL paths attached." was corrected to say "Hostnames may have URL paths included."
* This release fixes an issue where Scan Schedule didn’t work on the last Day of the Month for CDT Timezone. Scheduling a scan now works with any scenario.
* This release fixes an issue where when a CIDR IP had a semicolon or any other strange character at the end, the IP validation was not failing. This was corrected.
* This release resolves  an issue where the Log Executive Summary Report included Threat Manager sources. The report now only uses Log Manager sources.
* Prior to this release, the New Source creation form was displaying inapplicable items. This release corrects that and only applicable items now appear.
* This release resolves an issue where customers could not save Threat Manager configurations on newly spun up appliances. With this release, Threat Manager configurations can be saved, even if the appliance does not have a monitoring policy.

#### Features

None

#### Security

None

#### Changes

None

#### Notice

None
