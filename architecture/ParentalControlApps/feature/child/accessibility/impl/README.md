# `:core:accessibility`

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
  subgraph :feature:child
    direction TB
    subgraph :feature:child:accessibility
      direction TB
      :feature:child:accessibility:api[api]:::android-library
      :feature:child:accessibility:impl[impl]:::android-library
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
    subgraph :core:domain
      direction TB
      :core:domain:child[child]:::jvm-library
      :core:domain:common[common]:::jvm-library
    end
  end

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
