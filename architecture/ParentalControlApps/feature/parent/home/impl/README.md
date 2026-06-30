# `:feature:parent:home:impl`

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
  subgraph :feature:parent
    direction TB
    subgraph :feature:parent:home
      direction TB
      :feature:parent:home:api[api]:::android-library
      :feature:parent:home:impl[impl]:::android-library
    end
    subgraph :feature:parent:single-child
      direction TB
      :feature:parent:single-child:api[api]:::android-library
    end
    subgraph :feature:parent:subscription
      direction TB
      :feature:parent:subscription:api[api]:::android-library
    end
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
  subgraph :core
    direction TB
    subgraph :core:data
      direction TB
      :core:data:common[common]:::android-library
      :core:data:parent[parent]:::android-library
    end
    subgraph :core:domain
      direction TB
      :core:domain:common[common]:::jvm-library
      :core:domain:parent[parent]:::jvm-library
    end
  end
  subgraph :feature:common
    direction TB
    subgraph :feature:common:add-child
      direction TB
      :feature:common:add-child:api[api]:::android-library
    end
    subgraph :feature:common:auth
      direction TB
      :feature:common:auth:api[api]:::android-library
    end
  end
  subgraph :sync
    direction TB
    subgraph :sync:work
      direction TB
      :sync:work:common[common]:::android-library
      :sync:work:parent[parent]:::android-library
    end
  end

  :core:data:common -.-> :core:common
  :core:data:common -.-> :core:domain:common
  :core:data:common -.-> :core:network
  :core:data:common -.-> :core:notification
  :core:data:parent -.-> :core:common
  :core:data:parent -.-> :core:data:common
  :core:data:parent -.-> :core:domain:common
  :core:data:parent -.-> :core:domain:parent
  :core:data:parent -.-> :core:network
  :core:data:parent -.-> :sync:work:common
  :core:data:parent -.-> :sync:work:parent
  :core:domain:parent -.-> :core:domain:common
  :core:network -.-> :core:common
  :core:ui -.-> :core:designsystem
  :core:ui -.-> :core:domain:common
  :feature:common:add-child:api --> :core:navigation
  :feature:common:auth:api --> :core:navigation
  :feature:parent:home:api --> :core:navigation
  :feature:parent:home:impl -.-> :core:data:common
  :feature:parent:home:impl -.-> :core:data:parent
  :feature:parent:home:impl -.-> :core:designsystem
  :feature:parent:home:impl -.-> :core:domain:common
  :feature:parent:home:impl -.-> :core:domain:parent
  :feature:parent:home:impl -.-> :core:ui
  :feature:parent:home:impl -.-> :feature:common:add-child:api
  :feature:parent:home:impl -.-> :feature:common:auth:api
  :feature:parent:home:impl -.-> :feature:parent:home:api
  :feature:parent:home:impl -.-> :feature:parent:single-child:api
  :feature:parent:home:impl -.-> :feature:parent:subscription:api
  :feature:parent:single-child:api --> :core:navigation
  :feature:parent:subscription:api --> :core:navigation
  :sync:work:common -.-> :core:domain:common
  :sync:work:common -.-> :core:notification
  :sync:work:parent -.-> :core:common
  :sync:work:parent -.-> :core:domain:common
  :sync:work:parent -.-> :core:domain:parent
  :sync:work:parent -.-> :core:notification
  :sync:work:parent -.-> :sync:work:common

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
