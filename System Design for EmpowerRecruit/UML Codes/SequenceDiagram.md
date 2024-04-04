@startuml

actor Student as s #FF4500
actor Recruiter as r #FFD700
actor College as c #99FFFF
actor Admin as a #FFA07A

participant Website
participant StudentModule
participant RecruiterModule
participant CollegeModule
participant Jobs
participant Application
participant RecruiterProfile
participant CollegeProfile
participant StudentProfile
participant DriveDetails

a -> Website : Login
activate Website
Website -> AdminModule : Authenticate(username, password)
activate AdminModule
AdminModule -> Database : CheckCredentials(username, password)
activate Database
Database --> AdminModule : CredentialsValid
deactivate Database
AdminModule --> Website : AuthenticationSuccess
deactivate AdminModule
deactivate Website

a -> Website : ManageStudent(studentID)
activate Website
Website -> AdminModule : GetStudentDetails(studentID)
activate AdminModule
AdminModule --> Website : StudentDetails
deactivate AdminModule
Website --> a : DisplayStudentDetails
deactivate Website

a -> Website : ManageRecruiter(recruiterID)
activate Website
Website -> AdminModule : GetRecruiterDetails(recruiterID)
activate AdminModule
AdminModule --> Website : RecruiterDetails
deactivate AdminModule
Website --> a : DisplayRecruiterDetails
deactivate Website

a -> Website : ManageCollege(collegeID)
activate Website
Website -> AdminModule : GetCollegeDetails(collegeID)
activate AdminModule
AdminModule --> Website : CollegeDetails
deactivate AdminModule
Website --> a : DisplayCollegeDetails
deactivate Website

s -> Website : Login
activate Website
Website -> StudentModule : Authenticate(username, password)
activate StudentModule
StudentModule -> Database : CheckCredentials(username, password)
activate Database
Database --> StudentModule : CredentialsValid
deactivate Database
StudentModule --> Website : AuthenticationSuccess
deactivate StudentModule
deactivate Website

s -> Website : ViewJobOpenings
activate Website
Website -> Jobs : GetJobList
activate Jobs
Jobs --> Website : JobList
deactivate Jobs
Website --> s : DisplayJobList
deactivate Website

s -> Website : ApplyForJob(jobID)
activate Website
Website -> Application : CreateApplication(studentID, jobID)
activate Application
Application --> Website : ApplicationID
deactivate Application
Website --> s : ApplicationSubmitted
deactivate Website

s -> Website : ViewAppliedJobs
activate Website
Website -> Application : GetAppliedJobs(studentID)
activate Application
Application --> Website : AppliedJobList
deactivate Application
Website --> s : DisplayAppliedJobs
deactivate Website

r -> Website : Login
activate Website
Website -> RecruiterModule : Authenticate(username, password)
activate RecruiterModule
RecruiterModule -> Database : CheckCredentials(username, password)
activate Database
Database --> RecruiterModule : CredentialsValid
deactivate Database
RecruiterModule --> Website : AuthenticationSuccess
deactivate RecruiterModule
deactivate Website

r -> Website : ViewApplicants(jobID)
activate Website
Website -> Application : GetApplicants(jobID)
activate Application
Application --> Website : ApplicantList
deactivate Application
Website --> r : DisplayApplicants
deactivate Website

r -> Website : UpdateApplicationStatus(applicationID, status)
activate Website
Website -> Application : UpdateApplicationStatus(applicationID, status)
activate Application
Application --> Website : StatusUpdated
deactivate Application
Website --> r : ApplicationStatusUpdateSuccess
deactivate Website

r -> Website : ViewPostedJobs
activate Website
Website -> Jobs : GetPostedJobs(recruiterID)
activate Jobs
Jobs --> Website : PostedJobList
deactivate Jobs
Website --> r : DisplayPostedJobs
deactivate Website

r -> Website : ViewRecruiterProfile
activate Website
Website -> RecruiterProfile : GetRecruiterProfile(recruiterID)
activate RecruiterProfile
RecruiterProfile --> Website : RecruiterProfileData
deactivate RecruiterProfile
Website --> r : DisplayProfile
deactivate Website

c -> Website : Login
activate Website
Website -> CollegeModule : Authenticate(username, password)
activate CollegeModule
CollegeModule -> Database : CheckCredentials(username, password)
activate Database
Database --> CollegeModule : CredentialsValid
deactivate Database
CollegeModule --> Website : AuthenticationSuccess
deactivate CollegeModule
deactivate Website

c -> Website : ViewDriveDetails(driveID)
activate Website
Website -> DriveDetails : GetDriveDetails(driveID)
activate DriveDetails
DriveDetails --> Website : DriveDetailsData
deactivate DriveDetails
Website --> c : DisplayDriveDetails
deactivate Website

c -> Website : ViewCollegeProfile(collegeID)
activate Website
Website -> CollegeProfile : GetCollegeProfile(collegeID)
activate CollegeProfile
CollegeProfile --> Website : CollegeProfileData
deactivate CollegeProfile
Website --> c : DisplayCollegeProfile
deactivate Website

s -> Website : ViewStudentProfile(studentID)
activate Website
Website -> StudentProfile : GetStudentProfile(studentID)
activate StudentProfile
StudentProfile --> Website : StudentProfileData
deactivate StudentProfile
Website --> s : DisplayStudentProfile
deactivate Website

@enduml
