# `:feature:parent:intro:impl`

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
    subgraph :feature:parent:intro
      direction TB
      :feature:parent:intro:api[api]:::android-feature
      :feature:parent:intro:impl[impl]:::android-feature
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
    subgraph :feature:common:auth
      direction TB
      :feature:common:auth:api[api]:::android-feature
    end
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
  :feature:common:auth:api --> :core:navigation
  :feature:parent:intro:api --> :core:navigation
  :feature:parent:intro:impl -.-> :core:designsystem
  :feature:parent:intro:impl -.-> :core:domain:common
  :feature:parent:intro:impl -.-> :core:ui
  :feature:parent:intro:impl -.-> :feature:common:auth:api
  :feature:parent:intro:impl -.-> :feature:parent:intro:api

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
