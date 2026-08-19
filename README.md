# API Gateway

Single entry point for all client requests to the Pet Clinic microservices, routing traffic to the appropriate backend service.

## Student Information
- **Student Name:** Isuri Gamage
- **Student Number:** 241722008
- **Slack Handle:** 
- **GCP Project ID:** 

## Project Description
The `api-gateway` acts as the single entry point for the Pet Clinic system, routing incoming HTTP requests to the appropriate microservice (owner-service, pet-service, appointment-service) based on the request path. It uses Eureka for dynamic service discovery, so it does not need hardcoded service addresses, and integrates with the Config Server for centralized configuration. CORS is configured here to allow the frontend web application to communicate with the backend.

## Technology Stack
- **Language:** Java 25
- **Framework:** Spring Boot, Spring Cloud Gateway
- **Service Discovery:** Netflix Eureka Client
- **Configuration:** Spring Cloud Config Client
- **Build Tool:** Maven
- **Cloud Platform:** Google Cloud Platform (GCP) — deployed as IaaS on Compute Engine VM Instance Groups (multi-zone for high availability)
- **Process Management:** PM2

## Routing Configuration
| Path Pattern | Routed To |
|--------------|-----------|
| `/api/owners/**` | owner-service |
| `/api/pets/**` | pet-service |
| `/api/appointments/**` | appointment-service |

## Setup / Getting Started

### Prerequisites
- Java 25 (JDK)
- Maven
- Eureka Server and Config Server running
- owner-service, pet-service, and appointment-service running

### Steps
1. Clone the repository:
   ```bash
   git clone https://github.com/Isuri15/api-gateway.git
   cd api-gateway
   ```
2. Ensure `eureka-server` (port 8761) and `config-server` (port 8888) are running.
3. Build and run the service:
   ```bash
   mvn clean install
   mvn spring-boot:run
   ```
4. The gateway will start on port `8080` and route all `/api/**` requests to the appropriate microservice.

## Cloud Deployment
Deployed on Google Cloud Platform with multiple instances distributed across different zones within the region, fronted by a Cloud Load Balancer, to ensure high availability and fault tolerance.

## Related Repositories
This service is part of the Pet Clinic platform components. See the parent repository:
- [backend-microservices-platform](https://github.com/Isuri15/backend-microservices-platform)
