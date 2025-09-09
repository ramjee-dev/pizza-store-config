# Pizza Store Configuration Repository

This repository contains centralized configuration files for the Pizza Store microservices application.

## 🏗️ Architecture

The Pizza Store application uses Spring Cloud Config Server to manage configurations across multiple microservices:

- **Config Server**: Pulls configurations from this Git repository
- **Microservices**: Fetch their configurations from Config Server on startup

## 📁 Repository Structure
pizza-store-config/
├── application.yml # Default configuration for all services
├── application-dev.yml # Development environment
├── application-prod.yml # Production environment
├── auth-service.yml # Auth service specific config
├── auth-service-dev.yml # Auth service dev config
├── menu-service.yml # Menu service specific config
├── menu-service-dev.yml # Menu service dev config
├── order-service.yml # Order service specific config
├── order-service-dev.yml # Order service dev config
├── billing-service.yml # Billing service specific config
├── notification-service.yml # Notification service specific config
└── api-gateway.yml # API Gateway specific config


## 🚀 Usage

### Config Server Configuration

spring:
cloud:
config:
server:
git:
uri: https://github.com/YOUR-USERNAME/pizza-store-config
default-label: main


### Service Configuration
Services automatically fetch their configuration using:
- **Service Name**: `spring.application.name`
- **Profile**: `spring.profiles.active`
- **Label**: Git branch (default: main)

## 🔧 Configuration Precedence

1. **{service-name}-{profile}.yml** (highest priority)
2. **{service-name}.yml**
3. **application-{profile}.yml**
4. **application.yml** (lowest priority)

## 📝 Configuration Guidelines

- Use **environment-specific** profiles (dev, prod)
- Keep **sensitive data** in environment variables or vault
- Use **meaningful property names**
- Add **comments** for complex configurations

## 🔄 Refresh Configuration

To refresh configuration without restart:
curl -X POST http://localhost:8888/actuator/refresh


## 🌟 Services

| Service | Port | Description |
|---------|------|-------------|
| Config Server | 8888 | Configuration management |
| Eureka Server | 8761 | Service discovery |
| API Gateway | 8080 | API routing and security |
| Auth Service | 8081 | Authentication and authorization |
| Menu Service | 8082 | Menu and category management |
| Order Service | 8083 | Order processing |
| Billing Service | 8084 | Billing and payments |
| Notification Service | 8085 | Email and SMS notifications |

## 🔗 Related Repositories

- [Pizza Store Backend](https://github.com/YOUR-USERNAME/pizza-store-backend)
- [Pizza Store Frontend](https://github.com/YOUR-USERNAME/pizza-store-frontend)

---
*This configuration repository is part of the Pizza Store microservices architecture built with Spring Boot 3.5.5 and Java 21.*

