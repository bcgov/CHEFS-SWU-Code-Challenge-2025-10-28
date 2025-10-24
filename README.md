# Code Challenge – Notice, Instructions & Rules  
**Government Contact**: Daniel Pizarro - daniel.pizarro@gov.bc.ca
**Notice Date**: [2025-10-28] at 9:00 a.m. PT  
________________________________________
## 1. Applicability
These rules apply only to Shortlisted Proponents and form part of the RFP.  
## 2. Timeline
Shortlisted Proponents have 3 days from the Notice Date to complete the challenge.  
**Deadline**: 9:00 a.m. PT on [2025-10-31].  
## 3. Submission
Submit deliverables to this GitHub repository before the Deadline via a Pull Request to ```submission/<team-name>``` and tag the final commit v1.0.  
**Note**: CI is optional. Tests must run and pass locally (document commands in the README).
## 4. Eligible Resources
Only Proponent resources named in the RFP proposal may contribute.
## 5. Access
Eligible resources will receive GitHub invites to the private BCDevExchange-CodeChallenge organization.
## 6. Questions
Submit clarifying questions as they come up using GitHub Issues. Github issues submitted after 2:00 p.m. PT on [2025-10-30] will not be responded to.
## 7. Amendments
The Province may amend this notice before or after the Deadline; amendments will be posted in the repository.
## 8. Data & Privacy
Use fictional/test data only. Do not include PII. Submissions containing real personal data will be rejected.
## 9. Licensing & IP
Attach an Apache 2.0 license to your deliverable. By submitting, you grant the Province rights to use, reproduce, and modify the deliverables subject to the license.
________________________________________
# Problem Statement
- The BC Government is supporting education partners in modernizing school operations by replacing paper-based field trip permission slips with a secure, digital process.
- Current manual methods make it difficult to track, verify, and audit consent.
- This challenge asks proponents to design a small, digital prototype that demonstrates the use cases for how consent can be created, sent, tracked, and audited between teachers and parents.
- The goal is to model a **reusable, maintainable pattern that separates business logic from presentation** and could be adapted for other government consent or approval processes.
- Solutions should emphasize clarity, testability, and clean architecture, not production-level scale.
________________________________________  
## Use Cases (Required Capabilities)  
The challenge focuses on four core use cases that demonstrate key workflow and data-handling capabilities.  
### **Use Case A — Search Students (Seeded Data)**  
- **Actor**: Teacher/Admin
- **Goal**: Search students by Unique Student ID (S-########) or name (prefix/contains match acceptable).
- **Success**: Results list with basic details.   
### **Use Case B — Create & Send Consent Request**  
- **Actor**: Teacher/Admin
- **Goal**: Create a Field Trip record (date, location, transport), link it to a student, and Send a consent request to Parent/Guardian (simulation acceptable).
- **Success**: Consent transitions to Sent with timestamp + actor.   
### **Use Case C — Parent/Guardian Responds**  
- **Actor**: Parent/Guardian
- **Goal**: Provide a response to the consent request: Consented or Declined (optional notes).
- **Success**: Consent enters terminal state with timestamp + actor.  
### **Use Case D — View Consent Status**  
- **Actor**: Teacher/Admin
- **Goal**: View consent status for assigned students (Created, Sent, Consented, Declined).
- **Success**: List or detail view with current state and last-updated information.  
________________________________________  
# Non Functional Requirements  
## Consent Lifecycle  
- **States**: Created → Sent → (Consented | Declined) -> audit
- **Events** (record timestamp & actor for each): consent.created, consent.sent, consent.consented, consent.declined, consent.audit
- **Rationale**: Separating Created and Sent simplifies the model and aligns events with meaningful state changes.  
________________________________________   
## Audit  
Persist a server-side audit log of key events (create, send, consent, decline). Teacher checking the status is the auditing.  
________________________________________  
## Technical & Design   
- REST API for core flows with structured JSON error responses showing separation of the front end and back end.
- Lightweight, form-based UI with inline validation (required fields, email format, date constraints).
- Login and Authorization is not required.
- Testing: At least test is a unit test and at least one test is an integration test or an end to functional tests.
- Continuous Integration: Optional; document local test commands in README.
- Identify a few examples of accessibility compliance that you adhered to (e.g. WCAG 2.0 AA contrast of text on background).
- Data model diagram: specify the type of database and the model type you are using.  
________________________________________  
## Required Repository Structure  
```
/docs/ux
/docs/faq
/app
/app/api
/app/web
/scripts/seed
/tests/api
/tests/ui   (optional)
LICENSE
README.md
```
________________________________________
## Delivery 
- One-command setup with documentation (e.g. GitPod).
- Provide sample data.
- Demo covers all required use cases.
- At least 4 tests (one test per use case).
- Apache 2.0 license present.
- No PII.  
________________________________________  
# Summary of Deliverables  
- **README for your submission**: (setup, run, test, seed data, assumptions/limits).
- **UX artifacts**: wireframe(s), user journey diagram.
- **Demo**: in the format of a video or slide presentation (name files either ```demo.mp4``` or ```demo.pdf```) recommended length 10–15 min or 10 to 15 slides
- **Data model diagram**: data storage structure and relationships
- **working code**: covering the stated use cases and technical requirements
________________________________________  
# Evaluation Criteria (100 pts)  
- Use cases (40)
- Non functional requirements (20)
- Code quality & security best practices (10)
- Usability & UX clarity (15)
- Documentation quality & clarity (15)   
