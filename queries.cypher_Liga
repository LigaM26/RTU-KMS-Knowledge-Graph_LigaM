// Query 1: List study programmes MATCH (p:StudyProgram) RETURN p.programid AS ProgramID, p.title AS ProgramTitle, p.creditpoints AS CreditPoints;

// Query 2: Count courses per programme MATCH (p:StudyProgram)-[:HASCOURSE]->(c:Course) RETURN p.programid AS Program, count(c) AS NumberOfCourses ORDER BY NumberOfCourses DESC;

// Query 3: Display courses and credit points MATCH (p:StudyProgram)-[r:HASCOURSE]->(c:Course) RETURN p.programid AS Program, c.courseid AS Course, r.creditpoints AS CreditPoints, r.section_name AS Section ORDER BY Program, Course LIMIT 20;

// Query 4: Count learning outcomes per course MATCH (c:Course)-[:HASLEARNINGOUTCOME]->(lo:LearningOutcome) RETURN c.course_id AS Course, count(lo) AS LearningOutcomes ORDER BY LearningOutcomes DESC LIMIT 10;

// Query 5: Count topics per course MATCH (c:Course)-[:HASTOPIC]->(t:Topic) RETURN c.courseid AS Course, count(t) AS Topics ORDER BY Topics DESC LIMIT 10;
