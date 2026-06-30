# `:feature:child:home:impl`

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
    subgraph :feature:child:home
      direction TB
      :feature:child:home:api[api]:::android-library
      :feature:child:home:impl[impl]:::android-library
    end
    subgraph :feature:child:accessibility
      direction TB
      :feature:child:accessibility:api[api]:::android-library
    end
    subgraph :feature:child:youtube
      direction TB
      :feature:child:youtube:api[api]:::android-library
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
      :feature:common:auth:api[api]:::android-library
    end
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
  :core:ui -.-> :core:designsystem
  :core:ui -.-> :core:domain:common
  :feature:child:accessibility:api --> :core:navigation
  :feature:child:home:api --> :core:navigation
  :feature:child:home:impl -.-> :core:designsystem
  :feature:child:home:impl -.-> :core:domain:child
  :feature:child:home:impl -.-> :core:domain:common
  :feature:child:home:impl -.-> :core:ui
  :feature:child:home:impl -.-> :feature:child:accessibility:api
  :feature:child:home:impl -.-> :feature:child:home:api
  :feature:child:home:impl -.-> :feature:child:youtube:api
  :feature:child:home:impl -.-> :feature:common:auth:api
  :feature:child:youtube:api --> :core:navigation
  :feature:common:auth:api --> :core:navigation

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
