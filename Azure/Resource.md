## Service

Service is a representation of a functionality that Azure can provide.

## Resource

Resource is an instance of an Azure Service.
For example:  
+ Virtual Machine
+ App Service
+ Storage Account

## Resource Group

This is a group of resources used to logically group the related resources.

For instance we can group by environment: Development, Staging, Preproduction, Production

The naming convention is:
"rg-\<applicationName\>-\<group-descrimnator\>";

The metadata of the resource group can be stored in a different region than the resources within the group.

Resources in a group have the same life cycle.

Resources can interact with resources in other resources groups.

We can move a resource from one group to another.

The benefits of resource groups are:
- Administration is easier
- Cost management is easier
- Role-based access control (RBAC)

## Managment Group

Management group is a top level group that contain subscriptions. Subscriptions contains resource groups.
Resource groups contain resources. Management groups are used to manage different subscriptions:
for instance if company have multiple employees and they own subscriptions, we can manage access to different resource groups more easily.

Naming convention is similar to resource group but the prefix is "mg".

## Fault Domains

Fault domain is a group of resources that may fail at the same time due to the same root cause.
Each rack of servers is a separate fault domain. 
If the power supply or network switch fails, all the servers in that rack fails.

Fault Domain is physical grouping.

## Update Domains

An update domain is a group of resources that can be updated and rebooted if required at the same time.
Same updates require servers to be rebooted.
Only one update domain is rebooted at a time.

Update Domain is logical grouping.

## Availability Set

It is a set of resources that logically groups the isolated virtual machines resources from each other.
Virtual Machine placed in an Availability Set runs across multiple physical servers, compute racks, storage unites and network switches.
If a hardware of software failure happens, only a subset of Virtual Machines is impacted.

This is a concept in a single datacenter: physical grouping is Fault Domain, logical grouping is Update Domain.

Naming convention is similar to resource group but the prefix is "avail".

To create it search for "availability set". To add to this set we use ""Availability options".

It protects from failures within datacenter.

Important:
we can not add an existing Virtual Machine to an availability set after it was created.