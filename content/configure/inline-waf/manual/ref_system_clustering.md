# Clustering

The System Clustering page includes the following sections. Click on the link to go to the corresponding section to learn more:

<!--<MadCap:menuProxy mc-linked-toc="$topicHeadings" xmlns:MadCap="http://www.madcapsoftware.com/Schemas/MadCap.xsd" />-->
To go to the documentation for the previous section of System, see [System](ch_system.md). To go to  the documentation for next subsection in the System section, see [Configuration](ref_system_configuration.md).

To access the Clustering page in the **WAF** management interface, on the left panel, under System, click **Clustering**.

To save configuration changes or edits you make to any features and options, you must click **Save** on the lower-right of the section or page where you are making changes. Click **apply changes** on the upper-left corner of the page, and then click **OK**. Your changes will not be stored if you do not properly save your changes.

Clustering in WAF is based on VRRP. It allows for configuring high availability WAF pairs running Active/Passive with automatic fail-over within three seconds.

When deployed in combination with a load balancer in a separate load balancing pool many WAF nodes can be run Active/Active with the policy synchronized across all nodes by the master.

### Cluster virtual IP configuration

The Cluster virtual IP configuration section allows for adding new virtual interfaces with virtual IP addresses.

It is important that the exact same number of interfaces are configured on the master and worker and that the interfaces are configured in the same order.

<colgroup></colgroup>| **              Virtual IP            ** | Virtual IP address of the cluster. This is the IP address the nodes in the cluster are sharing. |
| **              Netmask            ** | The netmask defining the virtual IP's subnet. The netmask should be the same as the netmask assigned to the IP address of the physical interface to which Inbound Traffic is bound. |
| **              Interface            ** Drop down list | Which interface to bind the cluster intrface to..<dl><dt>                Options              </dt><dd>System interfaces</dd><dt>                Default              </dt><dd>First interface in the list</dd></dl> |
| **              Type            ** Drop down list | The type of the virtual IP.<dl><dt>                Options              </dt><dd>`FAILOVER MASTER` and `FAILOVER BACKUP`</dd><dt>                Default              </dt><dd>`FAILOVER MASTER`</dd></dl> To configure a failover IP address, on the master select `FAILOVER MASTER` and on the worker select FAILOVER BACKUP. See the examples below for more information. |

### Synchronization configuration

When Web Security Manager nodes are running a cluster one of the Web Security Manager nodes can be designated the TEACH role and the worker the LEARN role .

In order to keep load balancing and backup nodes up-to-date with the current configuration the TEACHER is keeping the LEARNER updated with changes to configured websites.

To keep the synchronization packages private in the cluster the messages are encrypted using a password as key. Synchronization messages can be sent using either MULTICAST or UNICAST.

<colgroup></colgroup>| **              Enable proxy settings synchronization            ** Check box | Enable or disable proxy settings synchronization. If enabled, Web Security Manager will synchronize the current ACL database and other parameters with other Web Security Manager nodes. |
| **              Mode            ** Drop down list | Synchronization role. If set to `Teach`, this Web Security Manager will multicast the ACL database to other Web Security Manager installations. If set to `Learn`, this Web Security Manager will update it's ACL database according to synchronization messages from other Web Security Manager installations. Synchronization settings affects the operation of the `Learner`. When synchronization is enabled and the node synchronization mode is set to `Learn`, the node will not sample learn data but wait for the node master to dispatch a policy. You need to configure an interface that will be used for synchronization before the ACL database synchronization will be activated. |
| **              Password            ** Input field | Password used for synchronization message authentication.<dl><dt>                Valid input              </dt><dd>Any string.
A long password is recommended as it do not have to be memorable by humans.</dd><dt>                Input example              </dt><dd>`98974953Q38512432324CU4859229842784`</dd><dt>                Default value              </dt><dd>`none`</dd></dl> |
| **              Protocol            ** Drop down list | Synchronization network protocol.<dl><dt>                Options              </dt><dd>`MULTICAST`
`UNICAST`</dd><dt>                Default              </dt><dd>`MULTICAST`</dd></dl> The MULTICAST method is selected by default. This method is the easiest to configure but as the name suggests the messages are sent to all nodes within the network and may not always work in complex networks. To keep network traffic at a minimum and to make things work in complex networks UNICAST should be preferred. This method requires the LEARN node to be specified on the TEACH node. When sending synchronization messages using UNICAST the TEACHER sends the messages directly to the LEARNERS ip address using UDP. |
| **              Sync type            ** Drop down list | How websites are synchronized are synchronized in a cluster.<dl><dt>                Options              </dt><dd>`FULL SYNC`
`TEMPLATE`</dd><dt>                Default              </dt><dd>`FULL SYNC`</dd></dl> This option applies to learning nodes and controls how websites are synchronized.<dl><dt>                FULL SYNC              </dt><dd>Everything, including "Listen IP", backend servers and health checking configuration is synchronized.
For HTTPS websites and HTTP websites configured to listen to a specific IP address it is required that the same IP addresses are configured on the learn node - typically in the form of a Cluster IP address configured for high availability or load balancing. Otherwise configuring the proxy core will fail.</dd><dt>                TEMPLATE              </dt><dd>When new website configuration is received by worker node: All information, including listen IP is included but website is created with disabled status meaning it will not served by the learning node until the website is enabled in ADC : [Virtual Host](ref_services_virtual_host.md).
When synchronizing changes Listen IP, backend server configuration, load balancing settings and health checking configuration will not be synchronized. This allows for synchronizing across datacenters or for synchronizing a cluster that is used in combination with a network load balancer.</dd></dl> |
| **              Peer(s)            ** Input field | The IP address(es) of the other node(s) in the cluster. This input field is disabled if `MULTICAST` is selected. In this case it displays the multicast address which cannot be changed.<dl><dt>                Valid input              </dt><dd>The IP address(s) of the corresponding node(s) in the cluster - i.e. on the TEACHER it should be the LEARNER(s) and vice versa.
Note that the IP address should be the IP address assigned to the network interface to which synchronization is bound on the corresponding node.
To synchronize to more than one LEARNER node using UNICAST add a list of LEARNER IP addresses separated by comma or space.</dd><dt>                Default value              </dt><dd>`none`</dd></dl> |

### Cluster configuration examples

Below are given examples of configuring a high availability cluster running in active/passive mode and a "self load balancing" cluster running in active/active mode.

#### Configuring a fail-over cluster

To configure a fail-over (active/passive) cluster of two Web Security Manager nodes do the following:

<table>
  <colgroup>
    <col />
    <col />
  </colgroup>
  <tbody>
    <tr>
      <td>
        <b>                Node 1 configuration              </b>
      </td>
      <td>
        <p>Create a FAILOVER-MASTER interface by doing the following:</p>
        <ol>
          <li>
            <p>In <b>Cluster virtual IP configuration</b> enter the virtual IP address of the cluster in the the <b>Virtual IP</b> field.                                    </p>
          </li>
          <li>
            <p>In <b>Netmask</b> enter the <code>netmask</code> specifying the subnet for the virtual ip.                                    </p>
          </li>
          <li>
            <p>Select the interface to bind the cluster interface to. If the configured cluster IP is within one of the system interfaces' netmask the system interface with the mask that matches must be selected.                                    </p>
          </li>
          <li>
            <p>In the Type drop-down menu select <code>FAILOVER-MASTER</code>.                                    </p>
          </li>
          <li>
            <p>Click the <b>Add virtual IP</b> button.                                    </p>
          </li>
        </ol>
        <p>Enable cluster synchronization and designate the role TEACH in the <b>Synchronization configuration</b> section:                           </p>
        <ol>
          <li>
            <p>Select <b>Enable proxy settings synchronization</b></p>
          </li>
          <li>
            <p>Select <code>TEACH</code> in the Mode drop-down.                                    </p>
          </li>
          <li>
            <p>Enter a password for the cluster in the <b>Password</b> field.                                    </p>
          </li>
          <li>
            <p>In the <b>Protocol</b> drop-down select the default <code>MULTICAST</code></p>
          </li>
          <li>
            <p>Click the <b>Save</b> button.                                    </p>
          </li>
        </ol>
      </td>
    </tr>
    <tr>
      <td>
        <b>                Node 2 configuration              </b>
      </td>
      <td>
        <p>Create a FAILOVER-BACKUP interface for the same virtual IP by doing the following:</p>
        <ol>
          <li>
            <p>In <b>Cluster virtual IP configuration</b> enter the virtual IP address of the cluster in the <b>Virtual IP</b> field.                                    </p>
          </li>
          <li>
            <p>In <b>Netmask</b> enter the <code>netmask</code> specifying the subnet for the virtual ip.                                    </p>
          </li>
          <li>
            <p>Select the interface to bind the cluster interface to. If the configured cluster IP is within one of the system interfaces' netmask the system interface with the mask that matches must be selected.                                    </p>
          </li>
          <li>
            <p>In the Type drop-down menu select FAILOVER-BACKUP.</p>
          </li>
          <li>
            <p>Click the <b>Add virtual IP</b> button.                                    </p>
          </li>
        </ol>
        <p>Enable cluster synchronization and designate the role LEARN in the <b>Synchronization configuration</b> section:                           </p>
        <ol>
          <li>
            <p>Select <b>Enable proxy settings synchronization</b></p>
          </li>
          <li>
            <p>Select <code>LEARN</code> in the Mode drop-down.                                    </p>
          </li>
          <li>
            <p>Enter the same cluster password as for node 1for the cluster in the <b>Password</b> field.                                    </p>
          </li>
          <li>
            <p>In the <b>Protocol</b> drop-down select the default <code>MULTICAST</code></p>
          </li>
          <li>
            <p>Click the <b>Save</b> button.                                    </p>
          </li>
        </ol>
      </td>
    </tr>
  </tbody>
</table>
The cluster can also be configured to synchronize and maintain fail-over state using UNICAST targeting a specific peer IP see [Synchronization configuration](#ref_system_cluster_sync.md) and [Cluster virtual IP configuration](#ref_system_clustering_vip.md) for more information.

### VRRP Interfaces

The **VRRP Interfaces** configuration section provides an overview of VRRP interfaces and allows for post configuration.

<colgroup></colgroup>| **              ID            ** | The VRRP interface id on the node. |
| **              VIP            ** | Virtual IP address of the cluster. This is the IP address the nodes in the cluster is sharing. |
| **              Netmask            ** | The netmask defining the virtual IP's subnet. |
| **Proto** |  |
| **Peer** |  |
| **              VHID            ** Input field | Virtual host identifier number of the VRRP group. On each Web Security Manager node VHIDs are required to be unique. VHIDs identify cluster groups accros Web Security Manager nodes. The same VHIDs are therefore required to be configured on both cluster nodes.<dl><dt>                Valid input              </dt><dd>An even integer in the range 2-254</dd><dt>                Default value              </dt><dd>`Next available VHID number`</dd></dl> |
| **              Interface            ** | The physical network interface the VRRP interface is bound to. |
| **              State            ** | State of the VRRP interface can be either `MASTER` or `BACKUP`. If a VRRP interface with a low priority (automatically set when selecting the types FAILOVER-BACKUP or LOADBALANCE-FAILOVER) is assuming the role of MASTER then probably the original MASTER node is experiencing problems. |
| **Type** |  |
| **              Priority            ** Input field | The priority of the interface in the VRRP group. Do not edit this property unless you are familiar with the VRRP protocol. The priority itself is an abstraction over the `advskev` VRRP parameter. When setting `priority``advskev` is calculated as `254 - priority`. Interfaces of type FAILOVER-MASTER are configured with a high priority and interfaces of type FAILOVER-BACKUP are configured with a lower priority.<dl><dt>                Valid input              </dt><dd>An integer in the range 1-254</dd><dt>                Default value              </dt><dd>`FAILOVER-MASTER: 254`
`FAILOVER-BACKUP: 154`</dd></dl> |
