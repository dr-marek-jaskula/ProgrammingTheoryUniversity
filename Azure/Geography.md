## Datacenter

Datacenter is a physical facility, where the data is stored. There are over 160 such facilities over the world. 
Datacenters contains thousands of physical racks of servers.
Facilities are heavily secured and protected. 

## Azure Geography

It is an area of the world that contains at least one Azure region. Usually geographies are countries. 
For instance: India, Greece, Norway, Austria, Italy, UK.
Microsoft will not store customer data outside the specified geography, except for certain non-regional services.

Geographies are used because:
- regulated data like financial, health care or credit data may not be allowed to leave the country
- placing the application closer to the users will enhance the performance

Sometimes there are more then one geography in a country, for instance:
- United Kingdom South, United Kingdom West

## Region

Each time we create a resource, we need to specify the region in which the resource will be stored.  
Azure region may also have an availability zones. Region contains at least one datacenter

## Region Pairs

Azure region may be paired to ensure BCDR:
- BC states for Business Continuity
- DR states for Disaster Recovery

Almost all region pairs are from the same geography:  
Canada Central - Canada East  
Central India - South India  
East US - West US  

There is one exception:  
Brazil South - South Central US

## Availability Zones

It is an unique physical location within the region.
Each Availability zone is made of one on more datacenters.
Not all regions have availability zones.
Region contains at least 3 availability zones if they are enabled.
We can think of a single availability zone as separate **Fault Domain** and **Update Domain**: 
for instance, if we have 3 availability zones, we have 3 Fault Domains and 3 Update Domains.

The concept of Fault Domains and Update Domains are still valid for zones.

It protects from entire datacenter failures.

## Cross-region resiliency

Resilience is the ability of a software to react to problems in one of its components and still provide the best possible service.

## Service Level Agreement (SLA)

Microsoft ensures:  
availability -> number of VMs
+ 99.9%  -> single VM
+ 99.95% -> Two or more VMs in a availability set
+ 99.99% -> Two or more VMs across two or more Availability Zones