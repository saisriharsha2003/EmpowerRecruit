@startuml

package "User Management" {
  [User] as user
  [Student] as student
  [Recruiter] as recruiter
  [College] as college
  [Admin] as admin
}

package "Job Management" {
  [JobPosting] as jobPosting
  [JobParsing] as jobParsing
}

package "Drive Management" {
  [DriveApproval] as driveApproval
}

package "Application Management" {
  [ApplicationProcessing] as appProcessing
  [ApplicationStatus] as appStatus
}

package "Profile Management" {
  [ProfileEditing] as profileEditing
}

package "Job Matching" {
  [MatchingAlgorithm] as matchAlgorithm
}

package "Database" {
  [UserDB] as userDB
  [JobDB] as jobDB
  [DriveDB] as driveDB
  [ApplicationDB] as appDB
}

user --> student
user --> recruiter
user --> college
user --> admin

student --> appProcessing : applyForJob(jobId)
recruiter --> jobPosting : postJob(jobDetails)
recruiter --> jobParsing : parse(jobDetails)
college --> driveApproval : approveDrive(driveId)

admin --> userDB : manageUsers()
admin --> jobDB : manageJobs()
admin --> driveDB : manageDrives()
admin --> appDB : manageApplications()

appProcessing --> matchAlgorithm : calculateCompatibility(applicantId, jobId)
appProcessing --> appStatus : updateStatus(applicationId, status)

userDB --> profileEditing : updateUserProfile(userId, profileData)

@enduml
