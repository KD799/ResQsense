# RESQSENSE
### Smart Disaster Response & Coordination Platform

**Connecting citizens, NGOs, and government rescue teams when every second matters.**

<p align="center">
  <a href="https://res-qsense-mu.vercel.app/"><strong>Live Demo</strong></a> ·
  <a href="https://github.com/Anvation-CSE-2026/ANV26-SC-06_ResQsense"><strong>GitHub Repository</strong></a>
</p>

---

## Overview

RESQSENSE is a disaster response and coordination platform designed to bridge the communication gap between citizens affected by natural disasters and the organizations responsible for emergency response.

During disasters, critical information is often scattered across multiple channels. Delayed verification, fragmented communication, and inefficient resource allocation can make it difficult to identify urgent incidents and coordinate an effective response.

RESQSENSE aims to bring incident reporting, disaster information, location awareness, incident prioritization, and rescue coordination into a unified platform.

The project is designed for three primary groups: **citizens, administrators and government authorities, and rescue organizations such as NGOs and emergency response teams.**

## Problem Statement

Disaster management requires timely information and coordinated action. Common challenges include:

- Fragmented communication between affected communities and rescue organizations.
- Difficulty validating incoming emergency reports.
- Limited visibility into incident severity and affected populations.
- Delays in prioritizing incidents and assigning appropriate rescue teams.
- Lack of a centralized view of incidents and rescue progress.
- Unreliable internet connectivity during emergency situations.

## Our Approach

RESQSENSE follows a structured response workflow:

**Detect → Validate → Prioritize → Assign → Rescue → Resolve**

1. **Detect:** Collect citizen reports and relevant disaster or weather information.
2. **Validate:** Evaluate report completeness, supporting evidence, and available sources.
3. **Prioritize:** Apply transparent, rule-based logic to estimate incident urgency.
4. **Assign:** Help administrators identify suitable rescue teams based on availability, capabilities, and location.
5. **Rescue:** Enable authorized teams to receive assignments and update their operational status.
6. **Resolve:** Record the final incident status and communicate relevant updates.

Critical assignments remain subject to authorized human review. The chatbot assists with information collection and communication; it does not independently determine emergency priority.

## Key Features

- **Location-aware incident reporting:** Capture emergency details and location information with user permission.
- **Interactive disaster map:** Visualize relevant incident locations and geographical information.
- **Incident validation:** Support report verification and duplicate detection.
- **Priority scoring:** Rank incidents using explainable rules and relevant risk factors.
- **Emergency chatbot:** Assist users with incident reporting and general disaster-safety information.
- **Disaster information centre:** Provide safety guidance and emergency-related information.
- **Role-based dashboards:** Offer separate interfaces for citizens, administrators, and rescue organizations.
- **Rescue coordination:** Support mission assignment and progress tracking.
- **Weather and disaster data integration:** Incorporate configured external data sources.
- **Real-time coordination:** Support timely dashboard updates where real-time services are configured.
- **Offline resilience:** A planned enhancement for queuing reports and synchronizing them when connectivity returns.

*Feature availability depends on the current implementation and service configuration.*

## User Roles

### Citizen Dashboard

- Submit emergency and disaster reports.
- View relevant incidents and location information.
- Access disaster safety guidelines.
- Use chatbot assistance.
- View incident and rescue status updates where available.

### Admin / Government Dashboard

- Review and verify submitted incidents.
- Monitor incident priority and status.
- Coordinate NGOs and rescue organizations.
- Approve and manage rescue assignments.
- Monitor operational progress.

### Rescue Team / NGO Dashboard

- View assigned rescue missions.
- Access incident details and locations.
- Manage team availability and capabilities.
- Update mission status and field progress.
- Report completion to the coordinating authority.

## Technology Stack

| Layer | Technology |
|---|---|
| Frontend | React |
| Backend and database services | Supabase |
| Database | PostgreSQL |
| Authentication | Supabase Auth, where configured |
| Mapping | Configured mapping provider |
| Deployment | Vercel |
| Version control | Git and GitHub |

Additional integrations, such as weather APIs, geospatial queries, real-time messaging, SMS notifications, and AI chatbot services, depend on the application's implementation and configuration.

## Architecture

```text
        CITIZENS / NGOs / AUTHORITIES
                    |
                    v
            RESQSENSE WEB APP
                 (React)
                    |
          +---------+---------+
          |         |         |
          v         v         v
       Reports   Dashboards  Chatbot
          |         |         |
          +---------+---------+
                    |
                    v
             SUPABASE SERVICES
          +---------+---------+
          |         |         |
          v         v         v
       Database   Auth      Storage
          |
          v
     Incident Records
          |
          v
    Validation & Priority
          |
          v
    Admin-Reviewed Assignment
          |
          v
      Rescue Coordination
```

This diagram represents the intended high-level architecture. Specific processing components and integrations may vary in the deployed implementation.

## Priority Scoring

The proposed priority engine considers relevant incident factors, such as:

- Severity of the reported emergency.
- Number of people affected.
- Immediate threats to human life.
- Environmental conditions and associated risks.
- Accessibility of the affected location.
- Available rescue resources.
- Reliability of the information received.

Priority and confidence are distinct concepts. **Priority** estimates the urgency of a response, while **confidence** represents the reliability of the supporting information.

Scores should remain explainable and subject to validation. They are decision-support indicators, not substitutes for professional assessment or official emergency instructions.

## Getting Started

### Prerequisites

- Node.js and npm.
- Git.
- Access to the repository.
- Supabase and mapping credentials if required by the current implementation.

### 1. Clone the repository

```bash
git clone https://github.com/Anvation-CSE-2026/ANV26-SC-06_ResQsense.git
cd ANV26-SC-06_ResQsense
```

### 2. Install dependencies

```bash
npm install
```

### 3. Configure environment variables

Create a `.env` file in the project root and add the variables required by the application.

For example, if these integrations are used:

```env
VITE_SUPABASE_URL=your_supabase_project_url
VITE_SUPABASE_ANON_KEY=your_supabase_public_key
VITE_MAPBOX_TOKEN=your_mapbox_public_token
```

Use the actual variable names expected by the codebase. Do not commit `.env` files containing credentials. Never expose service-role keys or private API secrets in frontend code.

### 4. Run the development server

```bash
npm run dev
```

Open the local URL displayed in the terminal.

### 5. Build the application

```bash
npm run build
```

The commands assume the repository uses the corresponding npm scripts. Check `package.json` if the available commands differ.

## Deployment

The application is deployed on Vercel.

- **Live application:** https://res-qsense-mu.vercel.app/
- **Source code:** https://github.com/Anvation-CSE-2026/ANV26-SC-06_ResQsense

To deploy a new version, push the relevant changes to the branch connected to the Vercel project, provided automatic deployments are configured.

## Security and Reliability

- Enforce database access policies using Supabase Row Level Security where applicable.
- Restrict privileged operations to authorized roles.
- Validate and sanitize submitted data.
- Protect personal information and precise location data.
- Keep private credentials out of frontend bundles and version control.
- Distinguish unverified reports from confirmed incidents.
- Provide clear feedback when location access or network connectivity is unavailable.
- Avoid treating automated priority scores as definitive emergency decisions.

## Future Scope

- Offline-first reporting and synchronization.
- Multilingual chatbot and safety information.
- Improved incident verification and duplicate detection.
- Integration with verified government disaster alerts.
- Enhanced geospatial risk assessment.
- Rescue resource optimization and route planning.
- Additional notification channels.
- Historical incident analytics and response-performance monitoring.

## Contributing

Contributions and suggestions are welcome.

1. Fork the repository.
2. Create a feature branch.
3. Implement and test your changes.
4. Commit your changes with a descriptive message.
5. Submit a pull request.

## Team

**Team Techmates**

Built by Badal, Krish, Aditya, and Kanai.

## Disclaimer

RESQSENSE is intended to support disaster awareness, incident reporting, and response coordination. It is not a replacement for official emergency services, verified government alerts, or professional rescue operations. In an actual emergency, contact the appropriate emergency services and follow official instructions.

---

**RESQSENSE — Detect early. Prioritize intelligently. Respond faster.**
