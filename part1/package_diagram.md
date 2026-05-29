# HBnB Architecture: High-Level Package Diagram

This document provides a conceptual overview of the three-layer architecture used in the HBnB application and illustrates the communication between these layers via the facade pattern.

## Package Diagram

The following diagram represents the structure of the application, focusing on the Presentation, Business Logic, and Persistence layers.

```mermaid
classDiagram
    class PresentationLayer {
        <<Package>>
        +API Endpoints
        +Services
    }

    class HBnBFacade {
        <<Facade>>
        +create_object()
        +get_object()
        +update_object()
        +delete_object()
    }

    class BusinessLogicLayer {
        <<Package>>
        +User Model
        +Place Model
        +Review Model
        +Amenity Model
    }

    class PersistenceLayer {
        <<Package>>
        +DatabaseAccessObjects
        +Data Repositories
    }

    %% Communication Pathways
    PresentationLayer --> HBnBFacade : Sends Requests
    HBnBFacade --> BusinessLogicLayer : Orchestrates Business Rules
    HBnBFacade --> PersistenceLayer : Delegates Storage & Retrieval
