# Data Modeling

A Data modeling document for any business data store.

!!! note

    This project will focus on the data modeling knowledge and implementation.

The end-to-end flow before implementation step.

```mermaid
---
title: E2E Flow
---
stateDiagram-v2
    direction LR
    R: Requirement Gathering
    D: Datasource Exploring
    T: Transform Spec
    
    [*] --> R

    R --> D
    D --> R: recheck logic
    D --> T
    T --> [*]
```

## Metadata

### Domain

### Transform Spec

The table structure for keeping transformation spec for any transform that use
on the ETL/ELT process.

### Control Framework
