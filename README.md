# Corbet Griffith - Career Infrastructure & Resume as Code

This repository houses the automated deployment pipeline for my professional resumes. I transitioned from static document files to a structured data approach to easily target specific roles in product management, ux design, and webdev.

## The Architecture
Instead of manually editing documents, my career history is stored as structured JSON. When an update is pushed to the `main` branch, a GitHub Actions workflow automatically triggers.

The CI/CD pipeline performs the following steps:
1. Spins up an Ubuntu environment and installs the required Node.js dependencies.
2. Parses the three targeted JSON files: `resume-tpm.json`, `resume-ux.json`, and `resume-bsa.json`.
3. Compiles the raw data into clean, ATS-optimized PDF files using the open source JSON Resume CLI.
4. Authenticates and pushes the freshly built PDFs directly to a Cloudflare R2 storage bucket.

## Tech Stack
* **Data Structure:** JSON Resume Schema
* **CI/CD:** GitHub Actions
* **Storage:** Cloudflare R2
* **Edge Delivery:** Cloudflare Workers (handles dynamic vanity URLs and A/B testing on my main domain)

## Why Build This?
Managing multiple versions of a resume is prone to version control errors. This system guarantees that whether a hiring manager is looking for a Technical Product Manager or a UX Engineer, they are always downloading the most accurate and up to date version of my experience. It also serves as a live demonstration of my ability to build and deploy automated digital infrastructure.