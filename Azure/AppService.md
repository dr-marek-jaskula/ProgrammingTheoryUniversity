## Azure App Service

It is a fully managed service for hosting:
- Web applications
- Mobile app backends
- RESTful APIs
- Automated business processes

App Service is Platform as a Service (PaaS)

Azure App Service features:
- Fully Managed Environment
- Multiple programming language and frameworks are supported
- Scalability
- Compliance 
- Security
- Containerization and Docker
- DevOps optimization
- Access on-premises data

## App Service Plan

To create App Service, we **need** an App Service Plan. It defines the compute resources required for your application to run.

Convention: use prefix "plan" for the App Service Plan

We can run more then one APP in App Service Plan. However, then they share same VM instances.
So all deployments slots also run on the same VM instances. Also WebJobs, diagnostic logs and backups operations
use CPU cycles and memory from the same VM instance.
Moreover, all apps are scaled together, based on the auto-scale setting.

## Azure Pricing Tier

There are three categories:
- Shared Compute
- Dedicated Compute
- Isolated

We can change pricing tier any time you want.

F1 in Dev/Test is free app service plan.

#### Shared Compute:
- Cannot scale out recourses
- Shared infrastructure
- All apps run on the same Azure VM (including apps of other customers)

#### Dedicated Compute:
- App run on dedicated VMs
- Only app in the same App Service plan share the same compute resources

#### Isolated:
- Dedicated virtual VMs and Virtual Networks
- Compute and network isolation
- Maximum scale-out capabilities