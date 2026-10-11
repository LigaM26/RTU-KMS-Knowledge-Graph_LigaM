**RTU KMS Knowledge Graph — Neo4j AuraDB**

1. **Introduction**

The objective of this project is to explore the RTU KMS Dataset, create a knowledge graph in Neo4j AuraDB, and analyse educational data using Cypher queries.

Dataset: https://github.com/ArithaRTU/KMS_Dataset

2. **Graph Schema**

The knowledge graph contains the following node labels:

- StudyProgram
- Course
- LearningOutcome
- Topic
- StudyField

The main relationships are:

- StudyProgram → Course (HAS_COURSE)
- Course → LearningOutcome (HAS_LEARNING_OUTCOME)
- Course → Topic (HAS_TOPIC)
- StudyProgram → StudyField (BELONGS_TO_FIELD)

3. **Database Overview**

Two study programmes were identified:

- DMB0 — Business Informatics, 120 credit points.
- HMD0 — Digital Humanities, 120 credit points.

The database contains 75 Course nodes, 366 LearningOutcome nodes, 640 Topic nodes, and 2 StudyProgram nodes. The StudyField label was also created.

The graph includes 79 programme-course relationships, 366 course-learning outcome relationships, and 640 course-topic relationships.

4. **Cypher Queries**
   
**Query 1: List Study Programmes**
MATCH (p:StudyProgram)
RETURN p.program_id AS ProgramID,
       p.title AS ProgramTitle,
       p.credit_points AS CreditPoints;


Result: DMB0 — Business Informatics and HMD0 — Digital Humanities, both with 120 credit points.

**Query 2: Count Courses per Programme**
MATCH (p:StudyProgram)-[:HAS_COURSE]->(c:Course)
RETURN p.program_id AS Program,
       count(c) AS NumberOfCourses
ORDER BY NumberOfCourses DESC;

Result:
- HMD0 — 50 courses.
- DMB0 — 29 courses.

**Query 3: Display Courses and Credit Points**
MATCH (p:StudyProgram)-[r:HAS_COURSE]->(c:Course)
RETURN p.program_id AS Program,
       c.course_id AS Course,
       r.credit_points AS CreditPoints,
       r.section_name AS Section
ORDER BY Program, Course
LIMIT 20;


Result: The query displays courses, their credit points, and curriculum sections.

**Query 4: Count Learning Outcomes per Course**
MATCH (c:Course)-[:HAS_LEARNING_OUTCOME]->(lo:LearningOutcome)
RETURN c.course_id AS Course,
       count(lo) AS LearningOutcomes
ORDER BY LearningOutcomes DESC
LIMIT 10;


Result: DE0717 has 11 learning outcomes, and DE0729 has 10.

**Query 5: Count Topics per Course**
MATCH (c:Course)-[:HAS_TOPIC]->(t:Topic)
RETURN c.course_id AS Course,
       count(t) AS Topics
ORDER BY Topics DESC
LIMIT 10;


Result: DE0810 has 20 topics. DE0809 and DE0814 each have 19.

5. **Conclusion**

The project demonstrates how Neo4j AuraDB can represent educational information as a knowledge graph. Five Cypher queries were used to explore study programmes, courses, credit points, learning outcomes, and topics.

The results show how graph databases can support curriculum exploration and analysis of relationships between educational entities.
