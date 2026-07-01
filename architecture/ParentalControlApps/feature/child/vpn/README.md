# `:feature:child:vpn:impl`

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
      :feature:child:vpn[vpn]:::android-feature
    end
  end
  subgraph :core
    direction TB
    :core:designsystem[designsystem]:::android-library
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
  subgraph :sync
    direction TB
    subgraph :sync:work
      direction TB
      :sync:work:common[common]:::android-library
    end
  end

  :core:domain:child -.-> :core:domain:common
  :core:ui -.-> :core:designsystem
  :core:ui -.-> :core:domain:common
  :feature:child:vpn -.-> :core:designsystem
  :feature:child:vpn -.-> :core:domain:child
  :feature:child:vpn -.-> :core:domain:common
  :feature:child:vpn -.-> :core:notification
  :feature:child:vpn -.-> :core:ui
  :feature:child:vpn -.-> :sync:work:common
  :sync:work:common -.-> :core:domain:common
  :sync:work:common -.-> :core:notification

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
