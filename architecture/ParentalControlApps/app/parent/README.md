# `:app:parent`

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
    :app:parent[parent]:::android-application
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
    subgraph :feature:common:youtube
      direction TB
      :feature:common:youtube:api[api]:::android-library
      :feature:common:youtube:impl[impl]:::android-library
    end
    subgraph :feature:common:auth
      direction TB
      :feature:common:auth:api[api]:::android-library
      :feature:common:auth:impl[impl]:::android-library
    end
  end
  subgraph :feature:parent
    direction TB
    subgraph :feature:parent:intro
      direction TB
      :feature:parent:intro:api[api]:::android-library
      :feature:parent:intro:impl[impl]:::android-library
    end
    subgraph :feature:parent:home
      direction TB
      :feature:parent:home:api[api]:::android-library
      :feature:parent:home:impl[impl]:::android-library
    end
    subgraph :feature:parent:single-child
      direction TB
      :feature:parent:single-child:api[api]:::android-library
      :feature:parent:single-child:impl[impl]:::android-library
    end
    subgraph :feature:parent:subscription
      direction TB
      :feature:parent:subscription:api[api]:::android-library
      :feature:parent:subscription:impl[impl]:::android-library
    end
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
  subgraph :sync
    direction TB
    subgraph :sync:work
      direction TB
      :sync:work:common[common]:::android-library
      :sync:work:parent[parent]:::android-library
    end
  end

  :app:parent -.-> :core:designsystem
  :app:parent -.-> :core:domain:common
  :app:parent -.-> :core:navigation
  :app:parent -.-> :feature:common:add-child:api
  :app:parent -.-> :feature:common:add-child:impl
  :app:parent -.-> :feature:common:auth:api
  :app:parent -.-> :feature:common:auth:impl
  :app:parent -.-> :feature:common:youtube:api
  :app:parent -.-> :feature:common:youtube:impl
  :app:parent -.-> :feature:parent:home:api
  :app:parent -.-> :feature:parent:home:impl
  :app:parent -.-> :feature:parent:intro:api
  :app:parent -.-> :feature:parent:intro:impl
  :app:parent -.-> :feature:parent:single-child:api
  :app:parent -.-> :feature:parent:single-child:impl
  :app:parent -.-> :feature:parent:subscription:api
  :app:parent -.-> :feature:parent:subscription:impl
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
  :feature:parent:intro:api --> :core:navigation
  :feature:parent:intro:impl -.-> :core:designsystem
  :feature:parent:intro:impl -.-> :core:domain:common
  :feature:parent:intro:impl -.-> :core:ui
  :feature:parent:intro:impl -.-> :feature:common:auth:api
  :feature:parent:intro:impl -.-> :feature:parent:intro:api
  :feature:parent:single-child:api --> :core:navigation
  :feature:parent:single-child:impl -.-> :core:designsystem
  :feature:parent:single-child:impl -.-> :core:domain:common
  :feature:parent:single-child:impl -.-> :core:domain:parent
  :feature:parent:single-child:impl -.-> :core:ui
  :feature:parent:single-child:impl -.-> :feature:common:youtube:api
  :feature:parent:single-child:impl -.-> :feature:parent:single-child:api
  :feature:parent:single-child:impl -.-> :feature:parent:subscription:api
  :feature:parent:subscription:api --> :core:navigation
  :feature:parent:subscription:impl -.-> :core:designsystem
  :feature:parent:subscription:impl -.-> :core:domain:common
  :feature:parent:subscription:impl -.-> :core:domain:parent
  :feature:parent:subscription:impl -.-> :core:navigation
  :feature:parent:subscription:impl -.-> :core:ui
  :feature:parent:subscription:impl -.-> :feature:parent:subscription:api
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
