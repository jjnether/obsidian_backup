
-   SEL Architect
-   Create IED's
-   Create dataset and transmit from proper IED
-   Receive proper bits from other IED, and assign to virtual bits


-   If there's an event, it bursts the sent message (default 4ms)
-   It then decays to its max time, where it sends at that max time while no events are going on (1s)
-   Doesn't need IP to function, it's based on MAC address
    -   You only need IP to send CID (upload goose config file to relay)
-   Must enable FTP (for sending the architect file), IEC 61850, and GOOSE in the port settings
- 0 is good GOOSE quality