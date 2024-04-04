@startuml

[*] --> Idle : Start

state Idle {
  [*] --> NotLoggedIn : Start
  NotLoggedIn --> LoggedInStudent : Student Login
  NotLoggedIn --> LoggedInRecruiter : Recruiter Login
  NotLoggedIn --> LoggedInCollege : College Login
  NotLoggedIn --> LoggedInAdmin : Admin Login
}

state LoggedInStudent {
  [*] --> ViewJobOpenings : View Job Openings
  ViewJobOpenings --> ViewJobDetails : Select a Job
  ViewJobDetails --> ApplyForJob : Apply for Job
  ApplyForJob --> ApplicationSubmitted : Submit Application
  ApplicationSubmitted --> ViewJobOpenings : Back to Job Openings
  ViewJobDetails --> ViewJobOpenings : Back
  ViewJobOpenings --> Logout : Logout
}

state LoggedInRecruiter {
  [*] --> PostJob : Post a Job
  PostJob --> ParseJob : Parse Job Details
  ParseJob --> ViewApplications : View Applications
  ViewApplications --> ProcessApplications : Process Applications
  ProcessApplications --> ViewApplications : Back
  PostJob --> Logout : Logout
}

state LoggedInCollege {
  [*] --> ViewDrives : View Placement Drives
  ViewDrives --> ApproveDrive : Approve Drive
  ApproveDrive --> ViewDriveDetails : View Drive Details
  ViewDriveDetails --> ViewDriveApplications : View Drive Applications
  ViewDriveApplications --> ViewStudentDetails : View Student Details
  ViewStudentDetails --> ViewSectionDetails : View Section Details
  ViewSectionDetails --> ViewStudentDetails : Back
  ViewDriveApplications --> ApproveApplication : Approve Application
  ApproveApplication --> ViewDriveApplications : Back
  ViewDrives --> Logout : Logout
}

state LoggedInAdmin {
  [*] --> ManageStudents : Manage Students
  ManageStudents --> AddStudent : Add Student
  AddStudent --> ManageStudents : Back
  ManageStudents --> RemoveStudent : Remove Student
  RemoveStudent --> ManageStudents : Back
  ManageStudents --> ViewStudentDetails : View Student Details
  ViewStudentDetails --> ManageStudents : Back

  [*] --> ManageRecruiters : Manage Recruiters
  ManageRecruiters --> AddRecruiter : Add Recruiter
  AddRecruiter --> ManageRecruiters : Back
  ManageRecruiters --> RemoveRecruiter : Remove Recruiter
  RemoveRecruiter --> ManageRecruiters : Back
  ManageRecruiters --> ViewRecruiterDetails : View Recruiter Details
  ViewRecruiterDetails --> ManageRecruiters : Back

  [*] --> ManageColleges : Manage Colleges
  ManageColleges --> AddCollege : Add College
  AddCollege --> ManageColleges : Back
  ManageColleges --> RemoveCollege : Remove College
  RemoveCollege --> ManageColleges : Back
  ManageColleges --> ViewCollegeDetails : View College Details
  ViewCollegeDetails --> ManageColleges : Back

  [*] --> ViewAllApplications : View All Applications
}

state ParseJob {
  [*] --> EnterJobDetails : Enter Job Details
  EnterJobDetails --> SubmitJob : Submit Job
  SubmitJob --> ParseSuccess : Parse Success
  ParseSuccess --> PostJob : Back to Post Job
  SubmitJob --> ParseFailure : Parse Failure
  ParseFailure --> EnterJobDetails : Retry
}

state ApplicationSubmitted {
  [*] --> ProcessingApplication : Processing Application
  ProcessingApplication --> SortApplications : Sort Applications
  SortApplications --> ViewApplications : View Applications
}

state Logout {
  [*] --> NotLoggedIn : Logout
}

NotLoggedIn --> Logout : Invalid Login

@enduml
