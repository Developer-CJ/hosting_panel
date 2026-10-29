Hosting Panel Control Center

A unified hosting management platform by CJIT Solutions.

                                            Plan. Test. Deliver. Support.

Hosting Panel Control Center (HPCC) is CJIT Solutions' planned central platform for managing customer hosting services from a single dashboard. The goal is to make provisioning, monitoring, and supporting hosted services straightforward for customers while giving CJIT a secure, centralized operations console.

The initial focus is FiveM server hosting, game-server databases, and related managed services, with an architecture that can expand to websites, applications, virtual servers, and other hosting products.

Project status: Active planning and development. This README describes the intended product and architecture; it does not imply that the listed capabilities are deployed, tested, or available to customers yet.

Vision

One portal for the full hosting lifecycle:

Customers can view their services, check health, request actions, and access support.

Administrators can provision infrastructure, manage accounts, review system activity, and respond to incidents.

Automation can handle routine deployment, monitoring, backups, and service maintenance with appropriate permissions and audit logs.

Planned Features

Area

Capabilities

Customer portal

Service dashboard, account management, usage, status, and support access

Service provisioning

Guided setup for FiveM hosting, databases, and future hosting products

Server management

Start, stop, restart, resource information, configuration, and operational logs

Database management

Provisioning, connection details, credential rotation, backups, and restore workflows

Monitoring

Availability checks, resource metrics, service alerts, and incident history

Billing integration

Plans, subscriptions, invoices, and service suspension workflows

Administration

Customer records, service inventory, access controls, and audit events

Automation

Provisioning jobs, scheduled maintenance, backup jobs, and notifications

These are product targets, not a list of verified implementations.

Architecture

HPCC follows a Cloudflare-first control plane with AWS-backed workloads. The control panel and its metadata can remain lightweight, while customer workloads run on infrastructure suited to their compute and storage requirements.

flowchart TD
    U["Customers and CJIT staff"] --> P["Cloudflare-hosted portal"]
    P --> A["Control API and authentication"]
    A --> M["D1: portal metadata"]
    A --> O["R2: approved artifacts"]
    A --> Q["Provisioning and job queue"]
    Q --> W["AWS hosting infrastructure"]
    W --> S["FiveM and application servers"]
    W --> D["Hosted databases"]

Technology Direction

Component

Intended role

Cloudflare Workers / Pages

Customer and administrator interfaces, API, routing, and orchestration

Cloudflare D1

Customer records, plans, service inventory, job metadata, and audit trails

Cloudflare R2

Approved deployment packages, artifacts, and suitable backup objects

AWS

Compute, networking, persistent storage, and database workloads where required

Secure provisioning agent

Executes approved infrastructure actions without exposing privileged credentials to the browser

The final service choices, capacity limits, and deployment topology will be confirmed during implementation and testing.

Example Use Case: FiveM Hosting

A customer subscribes to a FiveM hosting plan.

HPCC creates a tracked provisioning request.

An authorized backend process prepares the hosting environment.

The customer receives access to their service controls and permitted connection details.

HPCC reports health, usage, incidents, and scheduled backup status.

The platform is intended to support custom FiveM frameworks and deployment packages alongside the hosting service, while keeping client installations logically separated.

Security Principles

Hosting infrastructure requires stricter safeguards than an ordinary dashboard. HPCC is being designed around the following requirements:

Role-based access for customers, operators, and administrators.

Strong authentication and protected administrative actions.

Tenant isolation: one customer's data and services must not be accessible to another customer.

Server-side secret management; no AWS access keys, database passwords, or privileged tokens in client-side code or Git history.

Encrypted connections and private backend access where practical.

Audited provisioning, destructive actions, and permission changes.

Backups with documented retention, restore tests, and recovery procedures.

Resource limits and alerts to reduce runaway infrastructure costs.

Never commit .env files, API tokens, private keys, customer credentials, or production database exports to this repository.

Cost Strategy

The project aims to keep the control plane inexpensive by using suitable Cloudflare services and their available free allowances. Actual customer workloads may consume AWS compute, storage, bandwidth, IP addresses, backups, and other paid resources.

Free tiers are not a guarantee of zero cost. Hosting plans must account for real infrastructure usage, monitoring, backup retention, payment fees, and operational support before customers are provisioned.

Development Status & Roadmap

Establish repository structure and development environment

Implement authentication and customer/admin roles

Create the customer hosting dashboard

Define service plans, customer records, and metadata schema

Build the provisioning job queue and secure AWS integration

Add initial FiveM and database service templates

Implement health checks, metrics, alerts, and logs

Implement backup and restore workflows with verification

Integrate billing and subscription lifecycle

Complete security review, load testing, and production rollout

The checklist is intentionally unchecked until each milestone is implemented and verified in the project repository.

Getting Started

The installation and deployment workflow will be documented once the first runnable release is available. It will cover:

Required Node.js/Cloudflare tooling and AWS permissions.

Local development setup and environment configuration.

D1 database initialization and any migrations.

Secure provisioning-agent enrollment.

Automated tests, deployment, and post-deployment checks.

Do not deploy this README as if it were an installation guide. No production-ready installation commands have been established here yet.

Project Ownership

CJIT Solutions
Hosting Panel Control Center — part of the CJIT hosting and infrastructure ecosystem.

Website: cjitservices.tech

License

No open-source license has been selected. Until a LICENSE file is added, this repository is not offered under an open-source license. Contact CJIT Solutions for permission before reusing or distributing proprietary project material.

Hosting infrastructure made manageable — built and operated by CJIT Solutions.
