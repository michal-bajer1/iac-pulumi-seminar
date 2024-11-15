---
layout: section
class: text-center
---

# Pulumi

<div class="opacity-80 italic mb-4">
Using real code to manage infrastructure
</div>

---
layout: default
hideInToc: true
---

# What Makes Pulumi Different

## Specialized Domain Specific Language (DSL)
```hcl
# Terraform HCL
resource "azurerm_container_app" "example" {
  name                = "example-app"
  resource_group_name = azurerm_resource_group.example.name
}
```

## Real Programming Language
```csharp
// C# with Pulumi
var app = new ContainerApp("example-app", new ContainerAppArgs
{
    ResourceGroupName = resourceGroup.Name
});
```

<!--
# Speaker Notes

Setup:
- Compare approaches side by side
- Both define same resources
- Different developer experience

Key Points:
- Real languages vs DSL
- Full IDE support
- Type safety included

Questions/Engagement:
- "Which feels more natural?"
- "What advantages do you see?"

Next:
- See real-world example
-->

---
layout: center
hideInToc: true
---

# Real-World Example: Container App

```hcl {all|2-3|4-8|10-15|all}
resource "azurerm_container_app" "example" {
  name                         = "example-app"
  resource_group_name         = azurerm_resource_group.example.name
  container_app_environment_id = azurerm_container_app_environment.example.id
  revision_mode               = "Single"
  
  template {
    container {
      name   = "examplecontainerapp"
      image  = "mcr.microsoft.com/k8se/quickstart:latest"
      cpu    = 0.25
      memory = "0.5Gi"
    }
  }
}
```

<!--
# Speaker Notes

Setup:
- Common real-world scenario
- Multiple configuration levels
- Resource dependencies

Key Points:
- Configuration complexity
- Resource relationships
- Default handling
- Explain the basic Azure resources

Questions/Engagement:
- "What might be hard to maintain?"
- "How would you handle changes?"

Next:
- See same in Pulumi
-->

---
layout: center
hideInToc: true
---

# Same Resource in Pulumi

```csharp {all|1-2|4-5|7-13|all}
// Define container app with strongly-typed configuration
var app = new ContainerApp("example-app", new ContainerAppArgs
{
    ResourceGroupName = resourceGroup.Name,
    ManagedEnvironmentId = environment.Id,
    Template = new TemplateArgs
    {
        Containers = {
            new ContainerArgs
            {
                Name = "examplecontainer",
                Image = "mcr.microsoft.com/k8se/quickstart:latest",
                Resources = ContainerResources.GetResources(cpuCount: 0.25, gibibytesOfMemory: 0.5)
            }
        }
    }
});
```

<!--
# Speaker Notes

Setup:
- Same outcome, different approach
- Familiar C# patterns
- Strong typing benefits

Key Points:
- Type safety prevents errors
- IDE support helps
- Helper methods available

Questions/Engagement:
- "What C# features help here?"
- "How would you refactor this?"

Next:
- Build on this pattern
-->

---
layout: two-cols-header
hideInToc: true
---

# Building Abstractions

Turning infrastructure code into reusable components

::left::

## Raw Pulumi
```csharp {all|1-2|3-8|all}
// Basic database setup
var database = new Database("demo-db", new DatabaseArgs
{
    ResourceGroupName = resourceGroup.Name,
    ServerName = sqlServer.Name,
    Sku = new SkuArgs
    {
        Name = config.Get("database-sku")
    }
});
```

::right::

## High-level SDK
```csharp {all|1-2|3|4|all}
// High-level patterns
var database = new SqlDatabase("demo")
    .InResourceGroup(resourceGroup)
    .WithBasicTier();
```

<!--
# Speaker Notes

Setup:
- Evolution of infrastructure code
- Building team patterns
- Reducing complexity

Key Points:
- Raw: Full control
- High-level: Best practices
- Both have their place

Questions/Engagement:
- "Where would each fit?"
- "What would you abstract?"

Next:
- Core concepts overview
-->

---
layout: two-cols-header
hideInToc: true
---

# Core Concepts
Building blocks of Pulumi infrastructure

::left::

<div class="space-y-4">
  <div v-click class="concept-box">
    <div class="text-xl mb-2">📦 Projects</div>
    <ul class="text-sm">
      <li>Single unit of infrastructure</li>
      <li>Defines resources and patterns</li>
      <li>Version controlled together</li>
    </ul>
  </div>

  <div v-click class="concept-box">
    <div class="text-xl mb-2">🔧 Resources</div>
    <ul class="text-sm">
      <li>Individual cloud components</li>
      <li>Automatic dependency tracking</li>
      <li>Lifecycle management</li>
    </ul>
  </div>
</div>

::right::

<div class="space-y-4">
  <div v-click class="concept-box">
    <div class="text-xl mb-2">🏗️ Stacks</div>
    <ul class="text-sm">
      <li>Environment instances</li>
      <li>Configuration values</li>
      <li>Independent state</li>
    </ul>
  </div>

  <div v-click class="concept-box">
    <div class="text-xl mb-2">📊 State</div>
    <ul class="text-sm">
      <li>Resource tracking</li>
      <li>Change detection</li>
      <li>Team synchronization</li>
      <li>State locking</li>
    </ul>
  </div>
</div>

<style>
.concept-box {
  @apply p-4 rounded bg-gray-100 bg-opacity-10;
}
</style>

<!--
# Speaker Notes

Setup:
- Building blocks of Pulumi
- Each serves specific purpose
- Work together naturally

Key Points:
- Projects organize code
- Resources are cloud components
- Stacks separate environments
- State tracks everything

Questions/Engagement:
- "Similar to your project structure?"
- "Which concept is new?"

Next:
- See these in practice
-->

---
layout: two-cols-header
hideInToc: true
---

# Core Concepts #2

Examples of how Pulumi organizes infrastructure code

::left::

## Project
```yaml {all|2|3|4-5|all}
# Pulumi.yaml
name: container-app
runtime: dotnet
description: Base container app template
```

::right::

## Stacks
```yaml {all|2|3-4|5-6|all}
# Pulumi.dev.yaml
config:
  name: myapp-dev
  size: small
  location: westeurope
  resourceGroup: dev-rg
```
```yaml
# Pulumi.prod.yaml
config:
  name: myapp-prod
  size: large
  location: northeurope
  resourceGroup: prod-rg
```

<!--
# Speaker Notes

Key points to emphasize:
- Project = Template
  * One implementation
  * Shared across environments
  * Define patterns once
  * Version controlled together

- Stacks = Configurations
  * Environment-specific values
  * Different sizing/scaling
  * Regional settings
  * Resource naming

Questions to ask:
- "How is this similar to your application configs?"
- "What kind of values would you put in stack config?"
- "How might this help with environment consistency?"
-->
---
layout: default
hideInToc: true
---

# Projects and Stacks in Practice

## Project Code (Implementation)
```csharp {all|3-4|6-10|12-16|all}
public class MyStack : Stack
{
    // Constructor is the point of entry
    public MyStack()
    {
        // Get stack-specific values
        var config = new Config();
        var location = AzureLocation.FromId(config.Require("location"));
        var resourceGroup = AzureResourceGroup.Create($"mews-pulumi-example-{location.Abbreviation}-tmp", location);

        // Create resources
        var containerAppEnvironment = AzureContainerAppEnvironment.Create(
            name: $"pulumi-example-cae--{location.Abbreviation}",
            location: location,
            resourceGroup: resourceGroup,
            logDestination: new AzureMonitorDestination()
        );
    }
}
```
<!--
# Speaker Notes

Setup:
- Moving from concepts to code
- Constructor entry point
- Configuration handling

Key Points:
- Stack structure drives code
- Configuration management
- Resource organization

Questions/Engagement:
- "Where would you use stacks?"
- "What would you put in config vs code?"

Next:
- Look at stack operations
-->

---
layout: default
hideInToc: true
---

# Stack Operations
```bash {all|1-2|4-5|7-8|all}
# List available stacks
pulumi stack ls

# Switch to development stack
pulumi stack select dev

# View stack configuration
pulumi config
```

```bash
# Stack operations output
> pulumi config
KEY                 VALUE
location       westeurope
resourceGroup  dev-rg
name           myapp-dev
size           small
```

<!--
# Speaker Notes

Setup:
- Daily operations with stacks
- Common commands
- Configuration management

Key Points:
- Stack switching is easy
- Config per environment
- Clear separation

Questions/Engagement:
- "What would you configure?"
- "Which environments need separate stacks?"

Next:
- Understanding resources
-->

---
layout: center
hideInToc: true
---

# Understanding Resources

```mermaid {scale: 0.8}
graph TB
    A[Resource Group] --> B[Container App]
    A --> C[SQL Server]
    B -..->|Depends On| C
```

```csharp {all|1-2|4-5|7-8|all}
// Resource Definition
var resourceGroup = new ResourceGroup("rg-demo");

// Implicit Dependencies
var server = new SqlServer("sql-demo", new SqlServerArgs { ResourceGroupName = resourceGroup.Name });

// Explicit Dependencies
var app = new ContainerApp("app-demo", new ContainerAppArgs { ... }, new CustomResourceOptions { DependsOn = { server } });
```

<!--
# Speaker Notes

Setup:
- Resources are building blocks
- Dependencies matter
- Automatic ordering

Key Points:
- Implicit vs explicit deps
- Pulumi builds dependency graph
- Graph determines order
- Safe updates

Resource characteristics:
1. Unique identity
2. Tracked state
3. Dependencies
4. Lifecycle management

Questions/Engagement:
- "How do you handle dependencies without IaC?"

Next:
- State management
-->

---
layout: two-cols-header
hideInToc: true
---

# State Management

How Pulumi tracks your infrastructure

::left::

## State Example
```json {all|2-3|4-8|9-12|all}
{
   "version": 3,
    "deployment": {
        "manifest": {
            "time": "2024-11-07T10:20:28.011938947Z",
            "version": "v3.137.0"
        },
        "resources": [
            {
                "urn": "urn:pulumi:uuid",
                "custom": true,
                "id": "/subscriptions/*/resourceGroups/***/example",
                "type": "azure-native:app/v20230501:ManagedEnvironment",
                "outputs": {
                    // Values returned by Azure API for the resource
                }
            },
            // More resources
}
```

::right::

## Backend Options

- **Pulumi Cloud**
  * Managed state storage
  * Team collaboration
  * History and audit
  * RBAC support

- **Self-Hosted**
  * Azure Blob Storage
  * AWS S3

  <div className="fixed top-4 right-4 p-2 rounded bg-red-500 bg-opacity-20 border border-red-500 text-sm text-red-700 max-w-xs">
    <div className="font-bold mb-1">⚠️ Optional Slide</div>
  </div>

<!--
# Speaker Notes

Setup:
- State tracks everything
- Critical for operations
- Backend choices matter

Key Points:
- State is source of truth (or is it?)
- Records all resources
- Team collaboration needs

Questions/Engagement:
- "What happens if state is lost?"

Next:
- Working with state
-->

---
layout: center
hideInToc: true
---

# Working with State

## Common State Operations

```bash {all|1-2|4-5|7-8|10-11|all}
# View current state
pulumi stack

# Refresh state from cloud
pulumi refresh

# Export state backup
pulumi stack export --file backup.json

# Import state
pulumi stack import --file backup.json
```

## State & Reality

```mermaid {scale: 0.7}
graph LR
    A[Pulumi Code] --> B[Desired State]
    C[Current State] --> D[Actual Resources]
    B --> E{Compare}
    D --> E
    E -->|Different| F[Update Plan]
    E -->|Same| G[No Changes]
    style E fill:#f9f,stroke:#333
```

  <div className="fixed top-4 right-4 p-2 rounded bg-red-500 bg-opacity-20 border border-red-500 text-sm text-red-700 max-w-xs">
    <div className="font-bold mb-1">⚠️ Optional Slide</div>
  </div>

<!--
# Speaker Notes

Setup:
- State operations are critical
- Reality can drift
- Regular maintenance needed

Key Points:
- Refresh syncs state
- Export for backup
- Import for recovery

Questions/Engagement:
- "When might state drift?"
- "How would you prevent it?"

Next:
- Architecture overview
-->

---
layout: two-cols-header
hideInToc: true
---

# How Pulumi Works
Understanding the orchestration of infrastructure changes

::left::

```mermaid {scale: 0.5}
flowchart TB
    subgraph IDE ["Development Environment"]
        Code["Infrastructure Code 
        (C#, Python, etc.)"]
    end

    subgraph Pulumi ["Pulumi Engine"]
        LH["Language Host"]
        DE["Deployment Engine"]
        
        subgraph Providers ["Resource Providers"]
            Azure["Azure Provider"]
            AWS["AWS Provider"]
            K8s["Kubernetes Provider"]
        end
        
        LH --> DE
        DE --> Providers
    end

    subgraph Cloud ["Cloud Providers"]
        AzureCloud["Azure"]
        AWSCloud["AWS"]
        K8sCloud["Kubernetes"]
    end

    Code --> LH
    Azure --> AzureCloud
    AWS --> AWSCloud
    K8s --> K8sCloud
```

::right::

<div class="mt-4 space-y-4">
  <div v-click class="component-box">
    <div class="text-xl mb-2">Language Host</div>
    <div class="text-sm opacity-75">Executes your C# code and tracks resource declarations</div>
  </div>

  <div v-click class="component-box">
    <div class="text-xl mb-2">Deployment Engine</div>
    <div class="text-sm opacity-75">Orchestrates changes and manages state</div>
  </div>

  <div v-click class="component-box">
    <div class="text-xl mb-2">Resource Providers</div>
    <div class="text-sm opacity-75">Connect to cloud APIs and handle operations</div>
  </div>
</div>

<style>
.component-box {
  @apply p-4 rounded bg-gray-100 bg-opacity-10;
}
</style>

<!--
# Speaker Notes

Component Roles:

1. Language Host
   - Executes your C# code
   - Manages program runtime
   - Interprets resource declarations
   - Communicates with deployment engine

2. Deployment Engine
   - Heart of Pulumi
   - Compares desired vs current state
   - Orchestrates resource operations
   - Manages dependencies
   - Handles rollbacks

3. Resource Providers
   - Bridge to cloud APIs
   - Handle CRUD operations
   - Validate resource configurations
   - Report operation status

Flow explanation:
1. Your code runs in Language Host
2. Resource declarations sent to Deployment Engine
3. Engine determines required changes
4. Providers execute actual cloud operations

Key benefits:
- Separation of concerns
- Cloud-agnostic core
- Extensible provider model
- Native language experience

Questions to ask:
- "Where would you add new cloud support?"
- "What happens if a provider operation fails?"
-->
---
layout: center
hideInToc: true
---

# Architecture in Action

```mermaid {scale: 0.6}
sequenceDiagram
    participant IDE as Your Code
    participant LH as Language Host
    participant DE as Deployment Engine
    participant RP as Resource Provider
    participant Cloud as Azure

    IDE->>LH: new WebApplication("app")
    activate LH
    LH->>DE: Register resource
    activate DE
    DE->>DE: Check current state
    DE->>RP: Create resource
    activate RP
    RP->>Cloud: HTTP API call
    Cloud-->>RP: Response
    RP-->>DE: Operation result
    deactivate RP
    DE-->>LH: Resource created
    deactivate DE
    LH-->>IDE: Return resource reference
    deactivate LH
```

  <div className="fixed top-4 right-4 p-2 rounded bg-red-500 bg-opacity-20 border border-red-500 text-sm text-red-700 max-w-xs">
    <div className="font-bold mb-1">⚠️ Optional Slide</div>
  </div>

<!--
# Speaker Notes

Execution flow:
1. Code Declaration
   - Your C# code runs normally
   - Resource constructors create declarations
   - No cloud operations yet

2. Resource Registration
   - Language host tracks resources
   - Builds dependency graph
   - Sends to deployment engine

3. State Comparison
   - Engine checks existing state
   - Determines required changes
   - Plans operations

4. Provider Operations
   - Provider executes changes
   - Reports progress
   - Handles errors
   - Updates state

Key points:
- Async operations
- Error handling at each level
- State updates
- Progress reporting

Questions to ask:
- "Where could errors occur?"
- "How would rollback work?"
- "What happens if remote call fails?"

Next:
- Let's see real implementation
-->

---
layout: center
hideInToc: true
---

# Quick Questions

<div class="text-xl space-y-8">
  <div v-click class="question">
    What if I already created some resources manually?
  </div>

  <div v-click class="question">
    What if I losse my state storage?
  </div>
</div>

<style>
.question {
  @apply p-4 rounded bg-blue-500 bg-opacity-10 cursor-pointer hover:bg-opacity-20 transition-all;
}
</style>