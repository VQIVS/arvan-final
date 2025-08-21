# Arvan SMS Gateway

This README contains my document links, repository links, and everything I have accomplished for this task.

## Table of Contents
- [Document Links](#document-links)
- [Repository Links](#repository-links)

## High-Level Overview & Architecture

This project consists of two main microservices: **Finance Service** and **SMS Gateway Service**. Both services are containerized using Docker and communicate via RabbitMQ for asynchronous messaging. PostgreSQL is used as the primary database for both services.
For more details, refer to the documentation link above.
- [Project Documentation](https://docs.vqivs.sbs/share/5ea2vw6xnb/p/sms-gateway-YFg1SdPmw3)

## Repository Links

### Main Repositories
- [Finance Service](github.com/VQIVS/arvan-finance)
- [SMS Gateway Service](github.com/VQIVS/arvan-sms)


### Installation & Setup

#### Prerequisites
- Docker 
- Go 1.21+ 

#### Quick Start with Docker
1. **Clone both service repositories**
   ```bash
   # Clone Finance Service
   git clone https://github.com/VQIVS/arvan-finance.git
   
   # Clone SMS Service
   git clone https://github.com/VQIVS/arvan-sms.git
   ```

2. **Setup Finance Service**
   ```bash
   cd arvan-finance
   cp sample-config.json config.json
   # Edit config.json with your database credentials
   ```

3. **Setup SMS Service**
   ```bash
   cd ../arvan-sms
   cp sample-config.json config.json
   # Edit config.json with your database credentials
   ```

4. **Take the docker-compose.yml from arvan-final/docker**
   ```bash
    docker compose up -d 
    # if you want to use kong , then get kong configs from arvan-final too.
   ```

#### Manual Setup (Development)
1. **Clone repositories**
   ```bash
   git clone https://github.com/VQIVS/arvan-finance.git
   git clone https://github.com/VQIVS/arvan-sms.git
   ```

2. **Setup shared infrastructure (PostgreSQL & RabbitMQ)**
   ```bash
   cd arvan-finance
   docker compose up -d postgres rabbitmq
   ```

3. **Configure and run Finance service**
   ```bash
   cd arvan-finance
   cp sample-config.json config.json
   # Edit config.json with database and RabbitMQ credentials
   make run-dev
   ```

4. **Configure and run SMS service**
   ```bash
   cd ../arvan-sms
   cp sample-config.json config.json
   # Edit config.json with database and RabbitMQ credentials
   make run-dev
   ```

#### API Access
- Finance Service: `http://localhost:8080`
- SMS Service: `http://localhost:8081`
- RabbitMQ Management: `http://localhost:15672` (guest/guest)

### Testing
- **Run Finance service tests**: 
  ```bash
  cd arvan-finance && make test
  ```
- **Run SMS service tests**: 
  ```bash
  cd arvan-sms && make test
  ```