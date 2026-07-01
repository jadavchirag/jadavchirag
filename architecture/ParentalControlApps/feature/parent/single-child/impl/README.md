# `:feature:parent:child:impl`

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
    subgraph :feature:parent:single-child
      direction TB
      :feature:parent:single-child:api[api]:::android-feature
      :feature:parent:single-child:impl[impl]:::android-feature
    end
    subgraph :feature:parent:subscription
      direction TB
      :feature:parent:subscription:api[api]:::android-feature
    end
  end
  subgraph :core
    direction TB
    :core:designsystem[designsystem]:::android-library
    :core:navigation[navigation]:::android-library
    :core:ui[ui]:::android-library
  end
  subgraph :feature:common
    direction TB
    subgraph :feature:common:youtube
      direction TB
      :feature:common:youtube:api[api]:::android-feature
    end
  end
  subgraph :core
    direction TB
    subgraph :core:domain
      direction TB
      :core:domain:common[common]:::jvm-library
      :core:domain:parent[parent]:::jvm-library
    end
  end

  :core:domain:parent -.-> :core:domain:common
  :core:ui -.-> :core:designsystem
  :core:ui -.-> :core:domain:common
  :feature:common:youtube:api --> :core:navigation
  :feature:parent:single-child:api --> :core:navigation
  :feature:parent:single-child:impl -.-> :core:designsystem
  :feature:parent:single-child:impl -.-> :core:domain:common
  :feature:parent:single-child:impl -.-> :core:domain:parent
  :feature:parent:single-child:impl -.-> :core:ui
  :feature:parent:single-child:impl -.-> :feature:common:youtube:api
  :feature:parent:single-child:impl -.-> :feature:parent:single-child:api
  :feature:parent:single-child:impl -.-> :feature:parent:subscription:api
  :feature:parent:subscription:api --> :core:navigation

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
