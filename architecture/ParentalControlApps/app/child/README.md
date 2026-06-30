# `:app:child`

## Module dependency graph

<!--region graph-->
```mermaid
---
config:
  layout: elk
  elk:
    nodePlacementStrategy: SIMPLE
---
graph TB
  subgraph :app
    direction TB
    :app:child[child]:::android-application
  end
  subgraph :core
    direction TB
    :core:common[common]:::jvm-library
    :core:designsystem[designsystem]:::android-library
    :core:navigation[navigation]:::android-library
    :core:network[network]:::android-library
    :core:notification[notification]:::android-library
    :core:ui[ui]:::android-library
  end
  subgraph :feature:common
    direction TB
    subgraph :feature:common:add-child
      direction TB
      :feature:common:add-child:api[api]:::android-library
      :feature:common:add-child:impl[impl]:::android-library
    end
    subgraph :feature:common:auth
      direction TB
      :feature:common:auth:api[api]:::android-library
      :feature:common:auth:impl[impl]:::android-library
    end
    subgraph :feature:common:youtube
      direction TB
      :feature:common:youtube:api[api]:::android-library
      :feature:common:youtube:impl[impl]:::android-library
    end
  end
  subgraph :feature:child
    direction TB
    subgraph :feature:child:onboarding
      direction TB
      :feature:child:onboarding:api[api]:::android-library
      :feature:child:onboarding:impl[impl]:::android-library
    end
    subgraph :feature:child:home
      direction TB
      :feature:child:home:api[api]:::android-library
      :feature:child:home:impl[impl]:::android-library
    end
    subgraph :feature:child:accessibility
      direction TB
      :feature:child:accessibility:api[api]:::android-library
      :feature:child:accessibility:impl[impl]:::android-library
    end
    subgraph :feature:child:youtube
      direction TB
      :feature:child:youtube:api[api]:::android-library
      :feature:child:youtube:impl[impl]:::android-library
    end
  end
  subgraph :feature
    direction TB
    subgraph :feature:child
      direction TB
      :feature:child:calls-messages[calls-messages]:::android-library
      :feature:child:location[location]:::android-library
      :feature:child:vpn[vpn]:::android-library
    end
  end
  subgraph :sync
    direction TB
    subgraph :sync:work
      direction TB
      :sync:work:child[child]:::android-library
      :sync:work:common[common]:::android-library
    end
  end
  subgraph :core
    direction TB
    subgraph :core:data
      direction TB
      :core:data:child[child]:::android-library
      :core:data:common[common]:::android-library
    end
    subgraph :core:domain
      direction TB
      :core:domain:child[child]:::jvm-library
      :core:domain:common[common]:::jvm-library
    end
  end

  :app:child -.-> :core:designsystem
  :app:child -.-> :core:domain:child
  :app:child -.-> :core:domain:common
  :app:child -.-> :core:navigation
  :app:child -.-> :core:notification
  :app:child -.-> :core:ui
  :app:child -.-> :feature:child:accessibility:api
  :app:child -.-> :feature:child:accessibility:impl
  :app:child -.-> :feature:child:calls-messages
  :app:child -.-> :feature:child:home:api
  :app:child -.-> :feature:child:home:impl
  :app:child -.-> :feature:child:location
  :app:child -.-> :feature:child:onboarding:api
  :app:child -.-> :feature:child:onboarding:impl
  :app:child -.-> :feature:child:vpn
  :app:child -.-> :feature:child:youtube:api
  :app:child -.-> :feature:child:youtube:impl
  :app:child -.-> :feature:common:add-child:api
  :app:child -.-> :feature:common:add-child:impl
  :app:child -.-> :feature:common:auth:api
  :app:child -.-> :feature:common:auth:impl
  :app:child -.-> :feature:common:youtube:api
  :app:child -.-> :feature:common:youtube:impl
  :app:child -.-> :sync:work:child
  :app:child -.-> :sync:work:common
  :core:data:child -.-> :core:common
  :core:data:child -.-> :core:data:common
  :core:data:child -.-> :core:domain:child
  :core:data:child -.-> :core:domain:common
  :core:data:child -.-> :core:network
  :core:data:child -.-> :core:notification
  :core:data:common -.-> :core:common
  :core:data:common -.-> :core:domain:common
  :core:data:common -.-> :core:network
  :core:data:common -.-> :core:notification
  :core:domain:child -.-> :core:domain:common
  :core:network -.-> :core:common
  :core:ui -.-> :core:designsystem
  :core:ui -.-> :core:domain:common
  :feature:child:accessibility:api --> :core:navigation
  :feature:child:accessibility:impl -.-> :core:common
  :feature:child:accessibility:impl -.-> :core:designsystem
  :feature:child:accessibility:impl -.-> :core:domain:child
  :feature:child:accessibility:impl -.-> :core:domain:common
  :feature:child:accessibility:impl -.-> :core:network
  :feature:child:accessibility:impl -.-> :core:notification
  :feature:child:accessibility:impl -.-> :core:ui
  :feature:child:accessibility:impl -.-> :feature:child:accessibility:api
  :feature:child:calls-messages -.-> :core:designsystem
  :feature:child:calls-messages -.-> :core:domain:child
  :feature:child:calls-messages -.-> :core:domain:common
  :feature:child:calls-messages -.-> :core:ui
  :feature:child:home:api --> :core:navigation
  :feature:child:home:impl -.-> :core:designsystem
  :feature:child:home:impl -.-> :core:domain:child
  :feature:child:home:impl -.-> :core:domain:common
  :feature:child:home:impl -.-> :core:ui
  :feature:child:home:impl -.-> :feature:child:accessibility:api
  :feature:child:home:impl -.-> :feature:child:home:api
  :feature:child:home:impl -.-> :feature:child:youtube:api
  :feature:child:home:impl -.-> :feature:common:auth:api
  :feature:child:location -.-> :core:common
  :feature:child:location -.-> :core:domain:child
  :feature:child:location -.-> :core:domain:common
  :feature:child:location -.-> :core:notification
  :feature:child:location -.-> :feature:child:onboarding:api
  :feature:child:onboarding:api --> :core:navigation
  :feature:child:onboarding:impl -.-> :core:common
  :feature:child:onboarding:impl -.-> :core:data:child
  :feature:child:onboarding:impl -.-> :core:data:common
  :feature:child:onboarding:impl -.-> :core:designsystem
  :feature:child:onboarding:impl -.-> :core:domain:child
  :feature:child:onboarding:impl -.-> :core:domain:common
  :feature:child:onboarding:impl -.-> :core:notification
  :feature:child:onboarding:impl -.-> :core:ui
  :feature:child:onboarding:impl -.-> :feature:child:home:api
  :feature:child:onboarding:impl -.-> :feature:child:onboarding:api
  :feature:child:onboarding:impl -.-> :feature:common:add-child:api
  :feature:child:vpn -.-> :core:designsystem
  :feature:child:vpn -.-> :core:domain:child
  :feature:child:vpn -.-> :core:domain:common
  :feature:child:vpn -.-> :core:notification
  :feature:child:vpn -.-> :core:ui
  :feature:child:vpn -.-> :sync:work:common
  :feature:child:youtube:api --> :core:navigation
  :feature:child:youtube:impl -.-> :core:designsystem
  :feature:child:youtube:impl -.-> :core:domain:child
  :feature:child:youtube:impl -.-> :core:domain:common
  :feature:child:youtube:impl -.-> :core:ui
  :feature:child:youtube:impl -.-> :feature:child:youtube:api
  :feature:child:youtube:impl -.-> :feature:common:youtube:api
  :feature:common:add-child:api --> :core:navigation
  :feature:common:add-child:impl -.-> :core:designsystem
  :feature:common:add-child:impl -.-> :core:domain:common
  :feature:common:add-child:impl -.-> :core:ui
  :feature:common:add-child:impl -.-> :feature:common:add-child:api
  :feature:common:auth:api --> :core:navigation
  :feature:common:auth:impl -.-> :core:data:common
  :feature:common:auth:impl -.-> :core:designsystem
  :feature:common:auth:impl -.-> :core:domain:common
  :feature:common:auth:impl -.-> :core:ui
  :feature:common:auth:impl -.-> :feature:common:auth:api
  :feature:common:youtube:api --> :core:navigation
  :feature:common:youtube:impl -.-> :core:designsystem
  :feature:common:youtube:impl -.-> :core:domain:common
  :feature:common:youtube:impl -.-> :core:ui
  :feature:common:youtube:impl -.-> :feature:common:youtube:api
  :sync:work:child -.-> :core:common
  :sync:work:child -.-> :core:domain:child
  :sync:work:child -.-> :core:domain:common
  :sync:work:child -.-> :core:notification
  :sync:work:child -.-> :sync:work:common
  :sync:work:common -.-> :core:domain:common
  :sync:work:common -.-> :core:notification

classDef android-application fill:#CAFFBF,stroke:#000,stroke-width:2px,color:#000;
classDef android-feature fill:#FFD6A5,stroke:#000,stroke-width:2px,color:#000;
classDef android-library fill:#9BF6FF,stroke:#000,stroke-width:2px,color:#000;
classDef android-test fill:#A0C4FF,stroke:#000,stroke-width:2px,color:#000;
classDef jvm-library fill:#BDB2FF,stroke:#000,stroke-width:2px,color:#000;
classDef unknown fill:#FFADAD,stroke:#000,stroke-width:2px,color:#000;
```

<details><summary>📋 Graph legend</summary>

```mermaid
graph TB
  application[application]:::android-application
  feature[feature]:::android-feature
  library[library]:::android-library
  jvm[jvm]:::jvm-library

  application -.-> feature
  library --> jvm

classDef android-application fill:#CAFFBF,stroke:#000,stroke-width:2px,color:#000;
classDef android-feature fill:#FFD6A5,stroke:#000,stroke-width:2px,color:#000;
classDef android-library fill:#9BF6FF,stroke:#000,stroke-width:2px,color:#000;
classDef android-test fill:#A0C4FF,stroke:#000,stroke-width:2px,color:#000;
classDef jvm-library fill:#BDB2FF,stroke:#000,stroke-width:2px,color:#000;
classDef unknown fill:#FFADAD,stroke:#000,stroke-width:2px,color:#000;
```

</details>
<!--endregion-->
