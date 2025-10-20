# BMad Method - Universal Definition of Done

**Version:** 1.0
**Applies to:** All project types
**Date:** 2025-10-15

---

## Introduction

This document defines the universal criteria that must be met for a User Story or task to be considered "Done" when developing with BMad Method. These standards apply to all programming languages and project types to ensure delivery quality and consistency.

---

## General Criteria (General Criteria)

- [ ] **Code Complete (Code Complete):** All related code has been written.
- [ ] **Coding Standards Met (Coding Standards):** Code follows all norms defined in `docs/architecture/coding-standards.md`.
- [ ] **Peer Reviewed (Peer Reviewed):** Code has been reviewed by at least one other developer (Code Review), and all feedback has been addressed.
- [ ] **No Known Bugs (No Known Bugs):** At the time of delivery, there are no known bugs related to this Story.
- [ ] **Documentation Updated (Documentation Updated):** Related API documentation and usage guides have been updated accordingly.
- [ ] **Version Control (Version Control):** Changes have been committed to the appropriate branch and follow commit message norms.

---

## Development Standards (Development Standards)

- [ ] **Unit Tests Pass (Unit Tests Pass):** Unit tests have been written for new or modified business logic, and all test cases have passed.
- [ ] **Code Quality Checks Pass (Code Quality Checks Pass):** All code has passed Linter and formatting tool checks.
- [ ] **Security Review (Security Review):** Common security vulnerabilities have been checked (such as input validation, authentication, authorization, etc.).
- [ ] **Performance Considerations (Performance Considerations):** New feature performance impacts have been evaluated and ensured to meet performance standards.

---

## Testing and Quality (Testing & Quality)

- [ ] **Test Coverage Meets Standards (Test Coverage Meets Standards):** Code coverage reaches the minimum standard set by the project.
- [ ] **Integration Tests Pass (Integration Tests Pass):** Related module interactions and API endpoints have integration test coverage, and all test cases have passed.
- [ ] **Manual Testing Completed (Manual Testing Completed):** Key features have been validated through manual testing.
- [ ] **No Regression Bugs (No Regression Bugs):** Existing functionality has not been affected by new changes.

---

## Deployment and Delivery (Deployment & Delivery)

- [ ] **Build Successful (Build Successful):** The project can be built/packaged successfully with no errors.
- [ ] **Environment Compatibility (Environment Compatibility):** Functionality works normally in the target environment.
- [ ] **Deployment Ready (Deployment Ready):** All necessary deployment configurations and scripts have been prepared.
- [ ] **Rollback Plan (Rollback Plan):** An effective rollback strategy exists in case of deployment failure.

---

## Project-Specific Criteria (Project-Specific Criteria)

Depending on project type, additional completion standards may be needed:

### Web Applications
- [ ] **Cross-Browser Testing (Cross-Browser Testing):** Functionality works in supported browsers.
- [ ] **Responsive Design (Responsive Design):** Displays correctly across different screen sizes.
- [ ] **Accessibility (Accessibility):** Meets basic WCAG standards.

### API Services
- [ ] **API Documentation Updated (API Documentation Updated):** OpenAPI/Swagger documentation has been updated.
- [ ] **Backward Compatibility (Backward Compatibility):** Does not break existing API contracts.
- [ ] **Rate Limiting Tested (Rate Limiting Tested):** API rate limiting functionality works normally.

### Mobile Applications
- [ ] **Device Compatibility (Device Compatibility):** Works normally on target devices.
- [ ] **Offline Functionality Tested (Offline Functionality Tested):** Offline functionality works as expected.
- [ ] **App Store Requirements (App Store Requirements):** Meets app store publishing standards.