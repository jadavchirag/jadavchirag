# `:feature:child:location:impl`

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
  subgraph :feature
    direction TB
    subgraph :feature:child
      direction TB
      :feature:child:location[location]:::android-library
    end
  end
  subgraph :core
    direction TB
    :core:common[common]:::jvm-library
    :core:navigation[navigation]:::android-library
    :core:notification[notification]:::android-library
  end
  subgraph :core
    direction TB
    subgraph :core:domain
      direction TB
      :core:domain:child[child]:::jvm-library
      :core:domain:common[common]:::jvm-library
    end
  end
  subgraph :feature:child
    direction TB
    subgraph :feature:child:onboarding
      direction TB
      :feature:child:onboarding:api[api]:::android-feature
    end
  end

  :core:domain:child -.-> :core:domain:common
  :feature:child:location -.-> :core:common
  :feature:child:location -.-> :core:domain:child
  :feature:child:location -.-> :core:domain:common
  :feature:child:location -.-> :core:notification
  :feature:child:location -.-> :feature:child:onboarding:api
  :feature:child:onboarding:api --> :core:navigation

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
