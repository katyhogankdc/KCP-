# KCP-

Currently Enrolled Classes
```
select 
st.lastfirst AS StudentName, 
st.student_number AS StudentNumber,
st.grade_level AS Grade,
sch.abbreviation AS SchoolName, 
c.course_name AS Course, 
c.credit_hours AS CreditHours, 
c.credittype AS CreditType, 
schcc.dateenrolled AS DateEnrolled, 
schcc.dateleft AS DateLeft,
schcc.termid AS Term
from powerschool.powerschool_cc cc
JOIN powerschool.powerschool_students st on st.id = cc.studentid
JOIN powerschool.powerschool_schedulecc schcc on schcc.studentid = cc.studentid
JOIN powerschool.powerschool_courses c on c.course_number = schcc.course_number 
JOIN powerschool.powerschool_schools sch on sch.school_number = cc.schoolid
where schcc.dateenrolled >= '2017-08-01'
AND sch.abbreviation = 'KCP'
AND st.enroll_status = 0
```

Stored Grades
```

select 
sg.SchoolName AS School, 
st.student_number AS StudentNumber, 
st.lastfirst AS StudentName,
st.enroll_status AS EnrollmentStatus,
sg.grade AS LetterGrade, 
sg.earnedcrhrs AS EarnedCreditHours, 
sg.Course_name AS CourseName, 
sg.Credit_type AS SubjectArea,
sg.Grade_Level AS HistGradeLevel, 
sg.termbinsname AS Term,
st.grade_level AS CurrentGrade
from powerschool.powerschool_storedgrades sg
JOIN powerschool.powerschool_students st ON st.id = sg.studentid
```
