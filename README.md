HAM group for physical therapy | Mohammed
My Role Here

I was responsible for implementing core backend features of the physical therapy system. My contributions covered controllers, services, models, repositories, and utilities, with a strong focus on email notifications, PDF generation, booking management, and treatment plan automation.

📂 Controllers
BookingController (by Mohammed)

Create, update, and delete bookings between patients and doctors.

Retrieve patient bookings filtered by status and date range.

PatientController (by Mohammed)

Added an endpoint to request a PDF report for a patient from a doctor.

PlanController (by Mohammed)

Retrieve all treatment plans.

Add a new plan for a patient by a doctor.

Update an existing plan.

Delete a plan.

QuestionController (by Mohammed)

Retrieve all questions.

Add a new question.

Update an existing question.

Delete a question.

ReportController (by Mohammed)

Add a new report (with @RequestBody and @Valid).

Update an existing report (with @RequestBody and @Valid).

Generate a PDF report for a patient and doctor (dynamic filename + proper HttpHeaders).

VideoController (by Mohammed)

Upload a video for a patient in a specific plan.

Upload a video for a doctor in a specific plan.

📂 DTOs
BookingDTO (by Mohammed)

Appointment date validation using @FutureOrPresent and @NotNull.

Appointment day validation with the same constraints.

Applied @JsonFormat for correct date & time formatting.

PatientDTO (by Mohammed)

Added email field with validation.

Used @Email to enforce valid email structure.

Constraints applied with @NotEmpty and @Size(max = 30).

📂 Models
Doctor Model (by Mohammed)

Added email field.

Patient Model (by Mohammed)

Added email field.

(Fix by Hussam: @Column(columnDefinition = "varchar(30) unique not null")).

Plan Model (by Mohammed)

Added video list with @OneToMany relation (cascade = ALL, mappedBy = "plan").

Annotated with @JsonIgnore to prevent serialization issues.

📂 Repositories
BookingRepository (by Mohammed)

Added multiple query methods, including:

getBookingById(Integer id)

findByPatient_Id(Integer patientId)

findBookingByDoctor_Id(Integer doctorId)

findBookingByPatient_Id(Integer patientId)

findBookingByPatient_IdOrderByAppointmentDateDesc(...)

existsByDoctor_IdAndAppointmentDate(...)

existsByDoctor_IdAndAppointmentDateAfter(...)

existsBySchedule(Schedule schedule)

findBookingByAppointmentDateBetween(...)

PlanRepository (by Mohammed)

findPlanById(Integer id)

existsPlanByDoctor_IdAndPatient_Id(Integer doctorId, Integer patientId)

findVideosByPlanIdAndDoctorId(...) (custom query).

findPlanByIdAndPatient_Id(...)

findPlanByIdAndDoctor_Id(...)

QuestionRepository (by Mohammed)

findQuestionById(Integer id)

📌 Service Layer Contributions
BookingService (by Mohammed)

Email Notifications

Integrated EmailService into booking updates.

When status = "go-to-hospital", an instruction email is sent to the patient.

Automatic Plan Creation

When status = "go-to-plan", a new treatment plan is automatically created & linked.

Extra Endpoint

getPatientBookingsSimple(patientId, status, on, from, to)

Flexible filters by status, single date, or date range.

Results sorted by appointmentDate (ascending).

DoctorService (by Mohammed)

Welcome Email

Sends a welcome email to new doctors when registered.

Used emailService.sendWelcomeDoctorEmail(...).

Profile Update Notification

Sends an email when a doctor updates their profile.

📧 Email & PDF Services
EmailService (by Mohammed)

Fully implemented HTML-based email communication for doctors, patients, and hospital staff.

Uses Spring Boot JavaMailSender with styled templates.

Supports:

Welcome emails (patients & doctors).

Profile update confirmations.

Patient medical report distribution.

OpenHtmlToPdfGenerator (by Mohammed)

Implemented PDF generation directly from HTML.

Used for reports and email attachments.

ReportPdfService (by Mohammed)

Generates PDF files from Report objects.

ReportService (by Mohammed)

Added generatePdfReport to generate dynamic patient reports.

📄 Additional Contributions

Implemented QuestionService (CRUD).

Defined a PdfGenerator interface for flexible PDF generation.

Ensured proper validation, error handling, and messaging across services.
