```
graph TD
    A["Network Challenge Received"] --> B["Hashing Algorithm Initiates Target Query"]
    B --> C["OS Disk I/O Controller"]
    C --> D["Physical PCIe Bus"]
    C --> E["Random Chunk Read Request"]
    D --> F["NVMe Solid State Drive (Dataset)"]
    F == "Data Retrieval" ==> E
    E --> G["CPU Computes Hash of Retrieved Chunk"]
    G --> H{"Is Hash < Network Target?"}
    
    H -- YES --> I["Submit"]
    H -- NO --> J["Loop Next Read"]
    J -.-> B

```
