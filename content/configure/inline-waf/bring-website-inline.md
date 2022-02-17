# Bring Your Website Inline

You can deploy Alert Logic Managed Web Application Firewall (WAF) in one of two deployment modes: reverse proxy and routing proxy. The deployment mode you select determines how traffic passes through WAF.

## Understanding a proxy-based structure

In both deployment modes, WAF deploys as a proxy device. When WAF protects a website, traffic to that website passes through WAF before it reaches the backend web server. WAF is represented as the web server to the client while WAF is represented as the client to the web servers. This structure ensures that incoming traffic from the client is inspected and returned from the web servers.

## Reverse proxy

When deployed in reverse proxy mode, WAF serves traffic to the protected websites on one or more IP addresses. The website requests must direct traffic to the IP addresses to which WAF listens, as if it is the web server. You can set up this traffic flow several ways:

* Network Address Translation (NAT)
* DNS name resolving
* Load balancer

### Network Address Translation (NAT)

The firewall translates the public IP address to the new destination IP address WAF listens to.  You can change the IP address in the node that performs NAT.

In DNS, www.example.com resolves to 192.0.43.10.

In the network firewall, this address is translated to a private IP that is not accessible from the Internet address (e.g. 10.10.10.10).

When a request for 192.0.43.10 reaches the network firewall, the destination address is translated to 10.10.10.10 and the request is forwarded to that address.

WAF is then configured to listen on 10.10.10.11 for traffic to www.example.com and proxy it to 10.10.10.10.

The network firewall NAT rule needs to be changed from translate 192.0.43.10 to 10.10.10.10 to translate 192.0.43.10 to 10.10.10.11.

**To bring sites inline using the NAT rules method:**

1. Configure the website listen IP address based on one of the following options:

* Add a new website:
   1. On the Websites page, click **Add Website**.
   2. In the Listen IP list, select the address to add.

* Reconfigure an existing website:
   1. On the Websites page, select the website you want to reconfigure.
   2. Click **ADC**, and then click **Virtual host**.
   3. In the Listen IP list, click **Edit list** to add or remove the website you want.

1. Forward requests to the original web server IP address based on one of the following options:

* Add a new website:
   1. On the websites page, click **add a new website**.
   2. In the Real server IP or public domain name text box, and then type the web server IP address.

* Reconfigure an existing website:
   1. On the websites page, click the website you want to reconfigure.
   2. Click **ADC**, and then click **Load balancing**.
   3. Type the web server IP address in the Realhost/IP text box.

1. On the network firewall, reconfigure the NAT rule for the website that is configured as the listening IP in WAF. You must translate the public IP address to the private IP address.

### DNS—Name resolving

In DNS, you can reconfigure the web server domain name to point to an IP address that WAF listens to.

In DNS, www.example.com resolves to 192.0.43.10.

Assume the IP address, 192.0.43.11, is configured in WAF.

To send requests for www.example.com to 192.0.43.11 instead of 192.0.43.10, you must change the DNS record for www.example.com to 192.0.43.11.

After reconfiguration, the DNS could take several days to propagate properly in the Internet Domain Name System. Most organizations use private IP addresses with NAT and may also contribute to the delay for the DNS to propagate.

This DNS method can be effective for testing. The edited host file alters the DNS resolution for a single PC, which allows DNS to treat WAF as the origin of a website without affecting traffic.

Following the previous example, edit the hosts file and add the following line:

192.0.43.11 www.example.com

Common location of hosts file:

* Windows PC: %SystemRoot%\system32\drivers\etc\hosts
* Mac OS X: /etc/hosts
* Other: Wikipedia - hosts file

This action overrides the DNS lookup for that PC, resulting in the PC requesting 192.0.43.11 when connecting to www.example.com even though DNS reflects 192.0.43.10.

Alternatively, when one or more internal DNS servers are on the internal network, you can change the DNS record to point to the new IP address (192.0.43.11). This results in a limited group of users accessing the website through WAF (the ones using the local DNS server). Most of the other users will still access the website through the old IP address (192.0.43.10).

### Load balancer

If traffic to the website is through a load balancer, deployment and traffic direction to sites through WAF differ and is dependent on the load balancer in use.

For both load balancer options, the WAF IP address becomes the source IP of the client requests to the servers. The load balancing based on source hashing causes the load balancing decision to always direct to one server. Session persistence based on cookies or other client tokens work because WAF passes them through. If session persistence based on IP source hashing is desirable in a load balanced implementation, then the routing proxy deployment is recommended.

#### Configured as a Load Balanced Pool

You can configure one or more WAF appliances as a separate load balancing pool. The load balancer sends requests to the WAF pool before load balancing to the backend web servers.

The nodes in the WAF load balancing pool configure the load balancer as the backend web server. The WAF load balancing pool returns validated requests to the load balancer to decide what backend server to send the requests to.

#### Configured to Inspect Traffic Before the Load Balancer                        

You should configure the virtual IP address (VIP) that the load balancer serves for the website as the backend server IP.

#### Deployment after a load balancer

In routing proxy mode, you can deploy WAF behind network-layer, application-layer, and DNS-based load balancers.

You should add a static route to the load balancer that specifies WAF as the route to the web servers. This static route should not be on the firewall.

## Routing proxy

When you deploy a website in routing proxy mode, traffic destined for the website IP address is routed through WAF. When WAF listens to traffic from ports 80 and 443, this traffic goes through three steps:

1. The traffic is intercepted by a proxy service.
2. The traffic is validated.
3. The traffic is proxied to the backend IP.

In a routing proxy deployment, WAF does not configure listen IPs. The backend web server IP addresses become the listen IPs for WAF. If more than one backend web server serves a website, you must configure all the backend server IP addresses for the website in WAF.

### Static route

If you want to route traffic for the website IPs routed through WAF, you must add a static route. Alert Logic recommends that the static route be configured on the last node that routes or connects to the backend web server, the last layer three hop, which is typically is the network firewall, but can also be a load balancer.

If you deploy WAF in front of a load balancer, you must configure the listen IP of the load balancer as the backend server IP. If you connect WAF directly to the backend web server, the IP addresses of the backend server must be configured as real server IP.

**To add Real IP information in the WAF interface:**

Perform one of the following actions, based on your configuration:

* Add a new website:
   1. On the Websites page, click **Add Website**.
   2. In the **Real server IP** field, type the web server IP address.
* Reconfigure an existing website:
   1. On the Websites page, click the website you want to reconfigure.
   2. Click **ADC**, and then click **Load balancing** to find the **Realhost/IP** text box.
