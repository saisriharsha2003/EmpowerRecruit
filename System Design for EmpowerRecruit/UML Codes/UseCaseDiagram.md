@startuml

title EmpowerRecruit Usecase Diagram

left to right direction

actor Student as s #FF4500
actor College as c #99FFFF
actor Admin as a #FFA07A

rectangle "Student Interface" as studentInterface {
    usecase (Job Openings) as U1
    usecase (Apply for Jobs) as U2
    usecase (Applied Jobs) as U3
    usecase (Resume Parser) as U12
    usecase (Job Compatability Score) as U13
    usecase (Student Profile) as U14
}

rectangle "Recruiter Interface" as recruiterInterface {
    usecase (Post Jobs) as U4
    usecase (Posted Jobs) as U15
    usecase (View Applicants) as U5
    usecase (Update Application Status) as U6
    usecase (Recruiter Profile) as U16
    usecase (Job Parser) as U20
}
actor Recruiter as r #FFD700

rectangle "College Interface" as collegeInterface {
    usecase (Placement Drives) as U7
    usecase (Drive Details) as U8
    usecase (Companies) as U17
    usecase (Section Details) as U18
    usecase (College Profile) as U19
}

rectangle "Admin Interface" as adminInterface {
    usecase (Manage Student Profiles) as U9
    usecase (Manage Recruiter Profiles) as U10
    usecase (Manage College Profiles) as U11
}

s --> U1
s --> U2
s --> U3
s --> U12
s --> U13
s --> U14
s --> U15

r --> U4
r --> U5
r --> U6
r --> U15
r --> U16
r --> U20
r --> U17
r --> U7
r --> U3

c --> U7
c --> U8
c --> U17
c --> U18
c --> U19
c --> U15

a --> U9
a --> U10
a --> U11

@enduml
