# Customer Data Retention Policy

The policy for how long Alert Logic maintains customer data in its systems before permanent deletion varies according to data type. The schedule also depends on whether a customer still has an active account with Alert Logic or has ceased to have an active account. The policy is subject to individually contracted arrangements governing retention of a customer's data that has been negotiated with Alert Logic.

Some retention policies include both retention and deletion time frames. In this case, data will be deleted no sooner than the "retained for” period, and deleted no later than the "automatically deleted by” period.

Data retained after an account is deactivated is not accessible except for data export (by arrangement) or if the account is reactivated.

<table>
  <col />
  <col />
  <col />
  <col />
  <thead>
    <tr>
      <th>Data Type</th>
      <th>Description</th>
      <th>Active Account Retention Policy</th>
      <th>Inactive Account Retention Policy</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Asset knowledge</td>
      <td>Represents the documentation by Alert Logic of the customer deployments and environments such as hosts and networks </td>
      <td>Retained indefinitely</td>
      <td>
        <ul>
          <li>(Default) Automatically deleted by 13 months after the date of customer account termination</li>
          <li>(By request) Deleted manually after termination of a customer account upon written request</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>IDS events</td>
      <td>Input from the Alert Logic  Threat Manager appliances/agents and used as a basis to create incidents</td>
      <td>Retained for 6 months</td>
      <td>
        <ul>
          <li>(Default) Automatically deleted by 6 months after the date of customer account termination</li>
          <li>(By request) Deleted manually after customer account termination upon written request</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>File Integrity Monitoring (FIM) events</td>
      <td>Input from the Alert Logic FIM feature and used to analyze actions</td>
      <td> Retained for 12 months and automatically deleted by 13 months</td>
      <td>
        <ul>
          <li>(Default) Automatically deleted by 13 months after customer account termination</li>
          <li>(By Request) Expired manually after customer account termination upon written request<br /></li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>Log messages</td>
      <td>Input from the Alert Logic  Log Manager appliances/agents and used to correlate with IDS events data to create incidents and analyze incidents </td>
      <td> Retained for 12 months and automatically deleted by 13 months</td>
      <td>
        <ul>
          <li>(Default) Automatically deleted by 13 months after customer account termination</li>
          <li>(By Request) Expired manually after customer account termination upon written request<br /></li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>Scan and compliance</td>
      <td>Scan history and the resulting compliance results (if applicable) that are used to determine exposure/risk to a customer’s deployments and to consider against compliance initiatives such as payment card industry (PCI)</td>
      <td>
        <p> Retained for the later of:</p>
        <ul>
          <li>Three years after collection<br /></li>
          <li>Contracted data retention period for the customer account plus one month</li>
        </ul>
      </td>
      <td>
        <p>Automatically deleted by the later of:</p>
        <ul>
          <li> Three years after collection</li>
          <li>Contracted data retention period for the customer account plus one month after the date of customer account termination</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>
