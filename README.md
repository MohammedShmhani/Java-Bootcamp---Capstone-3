HAM Group for Physical Therapy | Mohammed
My Role

I developed core backend features of the physical therapy system, focusing on:

📅 Booking management

🩺 Treatment plan automation

📧 Email notifications

📄 PDF report generation

📂 Main Contributions
Controllers

BookingController → Manage bookings (create/update/delete + filter by status & date).

PatientController → Request patient PDF reports.

PlanController → CRUD for treatment plans.

QuestionController → CRUD for questions.

ReportController → CRUD + PDF report generation.

VideoController → Upload videos linked to plans (doctor & patient).

DTOs & Models

Added validation for booking dates & patient emails.

Extended Doctor & Patient models with unique email fields.

Enhanced Plan model with video relations.

Repositories

Custom queries for bookings, plans, and questions (filtering, existence checks, doctor/patient relations).

Services

BookingService → Email notifications & auto plan creation on booking updates.

DoctorService → Welcome + profile update emails.

EmailService → Complete email system (HTML templates, styled).

PDF Services → Generate reports directly from HTML (OpenHtmlToPdfGenerator, ReportPdfService).

✅ Key Impact

Automated booking & treatment workflows.

Enabled dynamic PDF reporting for patients and doctors.

Implemented email communication system (welcome emails, updates, medical reports).

Built reliable CRUD modules with proper validation and error handling.
