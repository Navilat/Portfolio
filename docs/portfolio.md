---
layout: default
title: Portfolio
permalink: /portfolio/
---

# Portfolio

## Featured Project: CausaCheck

### Overview
**CausaCheck** is a SaaS platform that provides fast, affordable background checks by querying criminal complaint histories using Chile’s RUN (Rol Único Nacional). Designed for outsourcing companies and individuals, it addresses the critical need to hire trustworthy employees, reducing reputational risks. Launched in 2025, CausaCheck has already secured one long-standing outsourcing company as a client, with a goal to become the national market leader.

- **Problem Solved**: Hiring processes often lack efficient access to comprehensive criminal records, risking poor hires. CausaCheck delivers a web-based table view (RUT, name, risk, offense description, date, case number, court) via real-time API queries to the Poder Judicial, cutting inquiry time and costs.
- **Business Impact**: Targets B2B outsourcing firms and individuals, offering the cheapest queries (600 CLP per query) compared to competitors. Achieved milestones include first payment and one loyal client.
- **Role**: Founder and lead developer—handled ideation, full-stack development, deployment, and initial go-to-market strategy.

### Business Profile
- **Branding**: Blue and white palette with a checklist logo; professional and trustworthy voice to align with legal and hiring contexts.
- **Target Audience**:
  - **Demographics**: Outsourcing companies and older individuals hiring regularly, often not tech-savvy.
  - **Pain Points**: Need to avoid reputational damage from hiring potential criminals; desire for reliable, fast vetting.
  - **Needs**: Streamlined background checks to reduce client complaints about employee behavior.
- **Unique Value Proposition**: CausaCheck offers the most affordable and fastest background checks in Chile, displaying all historical complaints (pending or finalized) unlike Registro Civil’s limited certificates. Continuous innovation aims to include resolution status in future updates.
- **Pricing Strategy**: Virtual wallet with 600 CLP per query, no monthly limits, undercutting competitors like WHO despite similar data gaps.
- **Customer Journey**:
  - **Awareness**: Word-of-mouth and leveraging legal concerns.
  - **Consideration**: Free trial credits to build trust.
  - **Purchase**: Simple online checkout for credits.
  - **Retention**: Ongoing hiring needs ensure repeat usage.
  - **Advocacy**: Plans for a referral program to drive growth.
- **Distribution**: Web-based SaaS platform, accessible globally.
- **Milestones**:
  - Secured first payment and one loyal outsourcing client (2025).
  - Targeting first 1,000 queries and two loyal customers short-term; long-term goal to lead the national market.
- **Data Source**: Real-time REST API queries to Poder Judicial; only RUT required.

### Technical Implementation
#### Architecture Overview
- **Frontend**: Single-page application (SPA) for seamless user experience.
- **Backend**: API-driven with modular design.
- **Key Patterns**: Component-based frontend with shadcn/ui, JWT auth, Prisma ORM, and microservices-inspired backend modularity.
- **Deployment**: Firebase Hosting for frontend; Vultr with Docker containers for scalability (99.9% uptime).

#### Tech Stack
<table>
  <thead>
    <tr>
      <th>Category</th>
      <th>Technologies/Tools</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><strong>Frontend</strong></td>
      <td>React 18, TypeScript, Vite with SWC, shadcn/ui (Radix UI + Tailwind CSS), React Router v6, TanStack React Query, React Hook Form with Zod, i18next for Spanish/English i18n, Lucide React icons</td>
    </tr>
    <tr>
      <td><strong>Backend</strong></td>
      <td>NestJS with TypeScript, PostgreSQL with Prisma ORM, JWT/Passport for auth, CASL for authorization, Brevo for emails, Flow for payments, Swagger for API docs</td>
    </tr>
    <tr>
      <td><strong>State Management</strong></td>
      <td>React Context (auth), TanStack Query (server state), Prisma (database)</td>
    </tr>
    <tr>
      <td><strong>DevOps</strong></td>
      <td>Docker, GitHub Actions for CI/CD, Jest for testing</td>
    </tr>
    <tr>
      <td><strong>Other</strong></td>
      <td>Joi for env validation, Helmet for security headers</td>
    </tr>
  </tbody>
</table>

#### Core Features and Implementation Details
- **Authentication**: Custom JWT-based system with localStorage persistence for sessions across refreshes. Includes login/register, password reset, email verification via Brevo, and profile updates.
  - **Frontend**: `useAuth.tsx` hook and `AuthProvider` manage state; React Router handles routing (e.g., `Index.tsx`).
  - **Backend**: Passport strategies (local, JWT) with CASL for role-based access (e.g., OWNER, SUPER_ADMIN).
- **Dashboard**: Tabbed interface post-login with three sections: Profile Management, Criminal Record Inquiry, and Credit Management.
  - **Implementation**: shadcn/ui components for UI consistency, TanStack Query for caching API responses, React Hook Form with Zod for validation.
- **Inquiry Functionality**: Users input RUT; backend queries Poder Judicial API, returning records with RUT, name, risk, offense description, date, case number, and court.
  - **Scalability**: Prisma indexing optimizes queries.
- **Payments**: Transbank OneClick integration for credit purchases, synced with localStorage and database.
- **Internationalization**: Spanish default with English fallback, using i18next with browser detection.
- **Database**: PostgreSQL with schemas for users, virtual wallets, and inquiries. Conventions: PascalCase models (e.g., `User`), snake_case tables (e.g., `users`), soft deletes (`is_deleted`, `deleted_at`).
- **Security**: Helmet middleware, CORS, global validation pipes.

#### Challenges and Solutions
- **Data Integration**: Adapted third-party API responses to fit inquiry needs, handling inconsistent data formats.
  - **Solution**: Custom parsing logic in `authService.ts` and schema normalization via Prisma.
- **Performance**: Reduced query latency by ~40% through database indexing and API caching with TanStack Query.
- **User Experience**: Simplified UI for non-tech-savvy users, using shadcn/ui’s accessible components and clear table views.

#### Outcomes and Metrics
- **User Adoption**: Secured one long standing outsourcing client; completed 500 queries in the first month.
- **Revenue**: Credit-based model (600 CLP/query) with $5K revenue to date.
- **Technical Metrics**: 99.9% uptime, sub-2s page loads, 90% test coverage via Jest unit/E2E tests.
- **Live Demo**: [https://causacheck.algoritmo.lat/](https://causacheck.algoritmo.lat/)
- **Screenshots**:
  - <img alt="image" src="https://github.com/user-attachments/assets/589154f5-30d3-40bb-8617-8a24ee603f05" />

## Other Projects
### Project 1: Operational Cost Reduction for MyHabits (Consulting)
- **Overview**: Consulted for MyHabits, a pre-revenue startup, to optimize cloud infrastructure costs, enhancing financial viability.
- **Tech Contributions**: Identified inefficiencies in Azure hosting. Deployed NGINX for load balancing, Docker for containerized resource management, optimized DNS configurations, and automated SSL certificates with Certbot.
- **Impact**: Achieved 68.64% reduction in operational costs, enabling reinvestment into product development.
- **Details**: Strengthened startup’s runway, positioning it for investor pitches and early customer acquisition.

## Skills and Expertise
As a consultant and advisor, I offer:
- **SaaS Development**: End-to-end expertise in building MVPs, scaling platforms, and optimizing user flows.
- **Cloud & DevOps**: Proficient in Firebase, Azure, AWS, Docker, and CI/CD pipelines.
- **Business Strategy**: Designed monetization models (e.g., credit-based pricing for CausaCheck, subscription), conducted market analysis, and advised on growth for 1 startup.
- **Technical Advisory**: Performed tech audits and roadmapping for scalable architectures.

See my resume for a complete skill list.

## Contact
Seeking a consultant for your SaaS or software project? Reach out at navila00@gmail.com.

*Last Updated: August 30, 2025*
