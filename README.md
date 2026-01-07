# HRMS - Human Resource Management System

A full-featured Human Resource Management System backend built with Spring Boot that connects job seekers with employers.

## Overview

HRMS is a comprehensive recruitment platform that enables:
- **Candidates** to create detailed profiles, manage CVs, and search for jobs
- **Employers** to post job advertisements and find qualified candidates
- **Employees** (HR staff) to manage the platform

## Features

### Candidate Management
- Profile creation with personal information
- Education history (university, faculty, department)
- Work experience tracking
- Language proficiency levels (1-5 scale)
- Technical skills management
- Social media and portfolio links
- Profile photo upload (via Cloudinary)

### Job Management
- Job advertisement creation and management
- Job position/title catalog
- City-based job filtering
- Active job listings with deadline tracking

### Authentication
- User registration for candidates and employers
- Email verification with activation codes
- Password validation

## Tech Stack

| Component | Technology |
|-----------|------------|
| Framework | Spring Boot 2.4.5 |
| Language | Java 11 |
| Build Tool | Maven |
| Database | PostgreSQL |
| ORM | Spring Data JPA / Hibernate |
| API Docs | Swagger 2.9.2 (Springfox) |
| Image Storage | Cloudinary |
| Code Generation | Lombok |

## Project Structure

```
HRMS/
├── src/main/java/kodlamaio/hrms/
│   ├── api/controllers/          # REST API endpoints
│   ├── business/
│   │   ├── abstracts/            # Service interfaces
│   │   └── concretes/            # Service implementations
│   ├── dataAccess/abstracts/     # JPA Repository interfaces
│   ├── entities/
│   │   ├── abstracts/            # Base entity classes
│   │   ├── concretes/            # Entity models
│   │   └── dtos/                 # Data Transfer Objects
│   ├── core/utilities/
│   │   ├── results/              # API response wrappers
│   │   ├── adapter/              # External service adapters
│   │   └── imageService/         # Image upload service
│   └── configuration/            # Spring configuration
├── src/main/resources/
│   └── application.properties    # Application configuration
└── pom.xml                       # Maven dependencies
```

## Prerequisites

- Java 11 or higher
- Maven 3.6+
- PostgreSQL 12+

## Installation

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd HRMS
   ```

2. **Create PostgreSQL database**
   ```sql
   CREATE DATABASE hrms;
   ```

3. **Configure database connection**

   Update `src/main/resources/application.properties`:
   ```properties
   spring.datasource.url=jdbc:postgresql://localhost:5432/hrms
   spring.datasource.username=your_username
   spring.datasource.password=your_password
   ```

4. **Build the project**
   ```bash
   ./mvnw clean install
   ```

5. **Run the application**
   ```bash
   ./mvnw spring-boot:run
   ```

   The application will start on `http://localhost:8080`

## API Documentation

Once the application is running, access the Swagger UI at:
```
http://localhost:8080/swagger-ui.html
```

### Main API Endpoints

| Endpoint | Description |
|----------|-------------|
| `/api/auth` | Authentication (register, verify email) |
| `/api/candidates` | Candidate management |
| `/api/employers` | Employer management |
| `/api/jobadvertisements` | Job postings |
| `/api/jobpositions` | Job position catalog |
| `/api/candidateschools` | Candidate education |
| `/api/candidateexperiences` | Candidate work history |
| `/api/candidatelanguages` | Candidate language skills |
| `/api/candidateskills` | Candidate technical skills |
| `/api/candidatelinks` | Candidate portfolio links |
| `/api/candidateimages` | Candidate profile photos |
| `/api/cities` | City reference data |

## API Response Format

All endpoints return standardized responses:

```json
{
  "success": true,
  "message": "Operation completed successfully",
  "data": { }
}
```

## Database Schema

### Core Entities
- **Users** - Base user entity (inherited by Candidates, Employers, Employees)
- **Candidates** - Job seekers with full profile support
- **Employers** - Companies posting job advertisements
- **JobAdvertisements** - Job postings with details and deadlines
- **JobPosition** - Job title/role reference data

### Candidate Profile Entities
- **CandidateSchool** - Education history
- **CandidateExperiences** - Work experience
- **CandidateLanguage** - Language proficiency
- **CandidateSkills** - Technical skills
- **CandidateLinks** - Portfolio/social links
- **CandidateImage** - Profile photos

### Reference Data
- **City** - Location data
- **University**, **Faculty**, **Department** - Education reference
- **Skills**, **Languages** - Skill/language catalogs
- **LinkTypes** - Social media link types

## Configuration

### Application Properties

| Property | Description | Default |
|----------|-------------|---------|
| `spring.datasource.url` | Database connection URL | `jdbc:postgresql://localhost:5432/hrms` |
| `spring.jpa.hibernate.ddl-auto` | Schema generation mode | `validate` |
| `spring.jpa.show-sql` | Log SQL queries | `true` |

### Cloudinary Configuration

Image uploads require Cloudinary credentials configured in `AppConfiguration.java`.

## Architecture

The project follows a layered architecture pattern:

1. **Controllers** - Handle HTTP requests and responses
2. **Services** - Business logic implementation
3. **Repositories** - Data access layer (Spring Data JPA)
4. **Entities** - Domain models mapped to database tables

## License

This project is developed for educational purposes.
