# `:feature:common:add-child:impl`

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
    subgraph :feature:common:add-child
      direction TB
      :feature:common:add-child:api[api]:::android-library
      :feature:common:add-child:impl[impl]:::android-library
    end
  end
  subgraph :core
    direction TB
    :core:designsystem[designsystem]:::android-library
    :core:navigation[navigation]:::android-library
    :core:ui[ui]:::android-library
  end
  subgraph :core
    direction TB
    subgraph :core:domain
      direction TB
      :core:domain:common[common]:::jvm-library
    end
  end

  :core:ui -.-> :core:designsystem
  :core:ui -.-> :core:domain:common
  :feature:common:add-child:api --> :core:navigation
  :feature:common:add-child:impl -.-> :core:designsystem
  :feature:common:add-child:impl -.-> :core:domain:common
  :feature:common:add-child:impl -.-> :core:ui
  :feature:common:add-child:impl -.-> :feature:common:add-child:api

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
