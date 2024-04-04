@startuml

|User|
start
:Login to the system;

if (User Type) then (Student)
  |Student|
  :View Job Openings;
  :Select a Job to Apply;
  if (Application Submitted?) then (yes)
    :Application Submitted;
    if (Application Accepted?) then (yes)
      :Job Offered;
      if (Accept Job Offer?) then (yes)
        :Accept Job Offer;
        :Job Accepted;
      else (no)
        :Reject Job Offer;
        :Job Rejected;
      endif
    else (no)
      :Application Rejected;
    endif
  else (no)
    :Submit Application;
  endif
 
elseif (User Type) then (Recruiter)
  |Recruiter|
  :Post a Job;
  :Parse Job;
  :Calculate Compatibility Score;
  :View Applications;
  :Process Applications;
  if (Application Approved?) then (yes)
    :Application Approved;
  else (no)
    :Application Rejected;
  endif
  
  :Edit Job Details;
  :Close Job;
elseif (User Type) then (College)
  |College|
  :View Placement Drives;
  :Approve Placement Drives;
  :View Drive Details;
  :View Drive Applications;
  if (Student Selected for Drive?) then (yes)
    :Student Selected for Drive;
  else (no)
    :Student Not Selected for Drive;
  endif
  :Edit Drive Details;
  :Cancel Drive;
elseif (User Type) then (Admin)
  |Admin|
  :Manage Students;
  :Add Student;
  :Remove Student;
  :View Student Details;
  :Manage Recruiters;
  :Add Recruiter;
  :Remove Recruiter;
  :View Recruiter Details;
  :Manage Colleges;
  :Add College;
  :Remove College;
  :View College Details;
  :View All Applications;
else
  :Invalid User Type;
endif

:Logout from the system;
stop

@enduml
