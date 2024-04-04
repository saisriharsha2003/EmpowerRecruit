@startuml

class User {
  - username: String
  - password: String
  - name: String
  - email: String
  - phoneNumber: String
  + login(): void
  + logout(): void
}

class Student {
  - resume: Resume
  + viewJobOpenings(): List<Job>
  + applyForJob(jobId: String): Application
  + editDetails(): void
}

class StudentProfile
{
  - studentProfile: object
  + updateProfile(studentProfile: object)

}
class RecruiterProfile
{
  - recruiterProfile: object
  + updateProfile(recruiterProfile: object)

}
class CollegeProfile
{
  - collegeProfile: object
  + updateProfile(collegeProfile: object)

}
class Recruiter {
  - jobProfile: JobProfile
  + postJob(jobDetails: String): Job
  + viewApplications(): List<Application>
  + processApplications(applicationIds: List<String>): void
}

class College {
  - drives: List<Drive>
  + viewDrives(): List<Drive>
  + approveDrive(driveId: String): void
  + viewDriveDetails(driveId: String): Drive
  + viewDriveApplications(driveId: String): List<Application>
}

class Admin {
  + manageStudents(): List<Student>
  + addStudent(studentDetails: String): Student
  + removeStudent(studentId: String): void
  + viewStudentDetails(studentId: String): Student
  + manageRecruiters(): List<Recruiter>
  + addRecruiter(recruiterDetails: String): Recruiter
  + removeRecruiter(recruiterId: String): void
  + viewRecruiterDetails(recruiterId: String): Recruiter
  + manageColleges(): List<College>
  + addCollege(collegeDetails: String): College
  + removeCollege(collegeId: String): void
  + viewCollegeDetails(collegeId: String): College
  + viewAllApplications(): List<Application>
}

class Resume {
  - resumeContent: object
  + parse(): void
}

class JobProfile {
  - jobDetails: String
  + parse(): void
}

class Drive {
  - driveId: String
  - driveDetails: String
  - status: String
  - startDate: Date
  - endDate: Date
  - location: String
  - company: String
  + approveDrive(driveId: String): void
}

class Job {
  - jobId: String
  - jobDetails: object
}

class Approve
{
  - application: List<Application>
  + approveApplication(applicationId: String): void
}

class Reject
{
  - application: List<Application>
  + rejectApplication(applicationId: String): void
}


class JobPosting
{
  - jobId: String
  - jobRole: String
  - jobOpenings: int
  - jobDescription: String
  - jobSalary: int
  - cgpa: double
  - experience: double
  + postJob(jobId: int): void
}

class Application {
  - applicationId: String
  - jobId: String
  - applicantId: String
  - status: String
  - compatibilityScore: double
  + getStatus(): String
  + setStatus(status: String): void
  + getCompatibilityScore(): double
  + setCompatibilityScore(score: double): void
}

User <|-- Student
User <|-- Recruiter
User <|-- College
User <|-- Admin

Student "1" -- "1" Resume
Recruiter "1" -- "1" JobProfile
College "1" -- "0..*" Drive
Job <.. Application : generates
Application -- Student : submitted by
Application -- Job : applied for
Recruiter -- Approve
Recruiter -- Reject
Recruiter -- JobPosting
College -- CollegeProfile
Recruiter -- RecruiterProfile
Student -- StudentProfile

@enduml
