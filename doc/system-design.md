# System chart

## System relationships diagram

The system relationships diagram is used to show the relationship 
between the system to be developed, the actors involved, and external systems.

```mermaid
%% https://mermaid.js.org/syntax/flowchart.html

flowchart LR
    %% Users
    %% {}: diamond
    AdminActor{Administrator}
    UseActor{Consumer}
    
    %% Use cases
    %% (): rounded rectangle
    CommonFormU(Cargo tracking view)
    AdminFormU(Cargo admin view)
    CargoSystemU(Cargo service)
    
    
    %% Notes
    %% []: rectangle
    N[The CargoTracker is sample application.
    It allows users to register cargo transport routes,
    to record and view the actual routes taken by cargo.
    It's based on the fictitious cargo transport system introduced in Eric Evans' DDD.
    ]
    
    %% Groups
    subgraph CargoTracker
        CargoSystemU
        subgraph form
            CommonFormU
            AdminFormU
        end
    end
    
    %% Arrows
    %% --> arrow, ==> bold arrow, --- line, -.- dotted line, === bold line
    UseActor --- CommonFormU
    AdminActor --- AdminFormU
    
    CommonFormU --- CargoSystemU
    AdminFormU --- CargoSystemU
    CargoTracker -.- N
```


## Use case diagram

```mermaid
%% https://mermaid.js.org/syntax/flowchart.html

flowchart LR
    %% Users
    %% {}: diamond
    AdminActor{Administrator}
    UseActor{Consumer}
    
    %% Use cases
    %% (): rounded rectangle
    TrackingFormU(Confirm cargo tracking status)
    ResisterFormU(Register new cargos)
    RouteFormU(Select the route to transport cargos)
    DestinationFormU(Update destination for cargos)
    EventFormU(Resister cargo events)
    
    %% Groups
    subgraph CargoTracker
        TrackingFormU
        
        subgraph admin-form
            ResisterFormU
            RouteFormU
            DestinationFormU
            EventFormU    
        end
    end
    
    
    %% Arrows
    %% --> arrow, ==> bold arrow, --- line, -.- dotted line, === bold line
    UseActor --- TrackingFormU
    AdminActor --- TrackingFormU
    AdminActor --- ResisterFormU
    AdminActor --- RouteFormU
    AdminActor --- DestinationFormU
    AdminActor --- EventFormU
```
