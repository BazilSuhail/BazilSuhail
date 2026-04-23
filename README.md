### System Architecture Flow

```mermaid
graph TD
    %% Node Definitions
    Start([Network Challenge Received])
    Query[Hashing Algorithm Initiates Target Query]
    OS[OS Disk I/O Controller]
    Bus[Physical PCIe Bus]
    SSD[(NVMe Solid State Drive - Dataset)]
    Read[Random Chunk Read Request]
    CPU[CPU Computes Hash of Retrieved Chunk]
    Decision{Is Hash < <br/>Network Target?}
    Submit([Submit])
    Loop[Loop Next Read]

    %% Flow Connections
    Start --> Query
    Query --> OS
    OS --> Bus
    OS --> Read
    Bus --> SSD
    SSD == "Data Retrieval" ==> Read
    Read --> CPU
    CPU --> Decision

    %% Decision Paths
    Decision -- YES --> Submit
    Decision -- NO --> Loop
    Loop -.-> Query
