# `:feature:child:auth:impl`

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
  subgraph :feature:common
    direction TB
    subgraph :feature:common:auth
      direction TB
      :feature:common:auth:api[api]:::android-feature
      :feature:common:auth:impl[impl]:::android-feature
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
    end
    subgraph :core:domain
      direction TB
      :core:domain:common[common]:::jvm-library
    end
  end

  :core:data:common -.-> :core:common
  :core:data:common -.-> :core:domain:common
  :core:data:common -.-> :core:network
  :core:data:common -.-> :core:notification
  :core:network -.-> :core:common
  :core:ui -.-> :core:designsystem
  :core:ui -.-> :core:domain:common
  :feature:common:auth:api --> :core:navigation
  :feature:common:auth:impl -.-> :core:data:common
  :feature:common:auth:impl -.-> :core:designsystem
  :feature:common:auth:impl -.-> :core:domain:common
  :feature:common:auth:impl -.-> :core:ui
  :feature:common:auth:impl -.-> :feature:common:auth:api

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
