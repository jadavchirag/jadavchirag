# `:feature:child:onboarding:impl`

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
    subgraph :feature:child:onboarding
      direction TB
      :feature:child:onboarding:api[api]:::android-library
      :feature:child:onboarding:impl[impl]:::android-library
    end
    subgraph :feature:child:home
      direction TB
      :feature:child:home:api[api]:::android-library
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
      :core:data:child[child]:::android-library
      :core:data:common[common]:::android-library
    end
    subgraph :core:domain
      direction TB
      :core:domain:child[child]:::jvm-library
      :core:domain:common[common]:::jvm-library
    end
  end
  subgraph :feature:common
    direction TB
    subgraph :feature:common:add-child
      direction TB
      :feature:common:add-child:api[api]:::android-library
    end
  end

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
  :feature:child:home:api --> :core:navigation
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
  :feature:common:add-child:api --> :core:navigation

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
