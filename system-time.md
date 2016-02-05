# System Date/Time

## Requirements (SRS)
1. Capability to update system time manually
2. Capability to sync via NTP periodically
3. Capability to sync via Cellular Base Station periodically
4. System time should be sync to hwclock once updated


## Views (SAS)

### Scenario
_<font color="gray">
The description of an architecture is illustrated using a small set of use cases, or scenarios which become a fifth view. The scenarios describe sequences of interactions between objects, and between processes. They are used to identify architectural elements and to illustrate and validate the architecture design. They also serve as a starting point for tests of an architecture prototype. This view is also known as **use case view**.
</font>_

#### Update time manually

#### Synchronize time via NTP server

#### Synchronize time via Cellular Base Station
1. _Admin_ navigate to `Settings`.`Time` page
2. _Admin_ select `Sync via Cellular` and configure schedule properly and `Save`

### Logical View
_<font color="gray">
The logical view is concerned with the functionality that the system provides to end-users. UML Diagrams used to represent the logical view include **Class diagram**, **Communication diagram**, **Sequence diagram**.
</font>_

### Development View
_<font color="gray">
The development view illustrates a system from a programmer's perspective and is concerned with software management. This view is also known as the implementation view. It uses the UML **Component diagram** to describe system components. UML Diagrams used to represent the development view include the **Package diagram**.
</font>_

### Process View
_<font color="gray">
The process view deals with the dynamic aspects of the system, explains the system processes and how they communicate, and focuses on the runtime behavior of the system. The process view addresses concurrency, distribution, integrators, performance, and scalability, etc. UML Diagrams to represent process view include the **Activity diagram**.
</font>_

### Physical view
_<font color="gray">
The physical view depicts the system from a system engineer's point of view. It is concerned with the topology of software components on the physical layer, as well as the physical connections between these components. This view is also known as the deployment view. UML Diagrams used to represent physical view include the **Deployment diagram**.
</font>_

## Test Cases (SAS)

### Case 1. Update time manually
### Case 2. Sync time via NTP Server
### Case 3. Failed to connect to NTP Server
### Case 4. Sync time via Cellular Base Station
1. Navigate to `Settings`.`Time` page.
2. Select `Manual` and configure time to an hour before. `Save`.
3. Select `Sync via Cellular` and configure schedule properly. `Save`.
4. Wait until the configured schedule is triggered.
5. Check Gateway time, which should be synced back.
6. Power cycle Gateway. Check Gateway time again, should be synced.

### Case 5. No signal while `Sync via Cellular`
### Case 6. Module not support while `Sync via Cellular`
### Case 7. No module while `Sync via Cellular`


## Design (SDS)

### Specification
System time support following 3 methods to update time.
 - Manually
 - Sync via NTP
    - NTP server
    - schedule interval (unit: seconds)
 - Sync via Cellular
    - schedule interval (unit: seconds)

### Man Page
```
NAME
    mxcellular - cellular utility

SYNOPSIS
    mxcellular --sync-time [OPTIONS]

DESCRIPTION
    --sync-time
        Synchronize system time through Cellular Base Station.
    --retry n
        Retry the command n times if failed.
    --retry-delay n
        Delay n msecs before retry the command.

        Example:
        $ sudo mxcellular --time-sync
        2016/01/13 16:37:28

EXIT STATUS
    0
        Gracefully terminated.
    1
        Not support.
    2
        Unknown error.
```
