---
layout: page
active: syllabus
title: Syllabus
---


# Syllabus for CSC 476: {{ site.data.course.title }}

* **Instructor:** Ian Dunn
* **Office:** Building 14, Room 209
* **Office Hours:** MWF 11:10am - 12:00pm
* **Email:** idunn01@calpoly.edu
* **Schedule:**
  * Lecture: {{ site.data.course.meetings.lecture.when }} ({{ site.data.course.meetings.lecture.in }})
  * Lab: {{ site.data.course.meetings.lab.when }} ({{ site.data.course.meetings.lab.in }})
* **Website:** [https://iondune.github.io/csc476/](https://iondune.github.io/csc476/)



## General:

Welcome to 3D game development.
This course will teach you *some* of the important *computer graphics principals* of 3D games.
This course is primarily focused on the graphics components of interactive 3D games/worlds.
We will cover advanced real-time graphics techniques mostly in the context of games.
**This course requires substantial math and programming skills.**
Experience with C or C++ will be essential and experience with linear algebra will be very helpful.
We will be using OpenGL and GLSL for our graphics APIs, along with C++ to create computer graphics games throughout the quarter.
You are welcome to develop your programs under varying operating systems
as long as the final programs can be demonstrated and run on multiple machines for the final gameplay demo.



## Course Objectives

By the end of the quarter, students will:

- Understand and master the graphics pipeline and the basic implementation of the
  pipeline in modern hardware (and graphics libraries)
- Understand programmatic choices related to geometry in real-time games,
  including understanding basic vocabulary, general computation and understanding
  of trade-offs of:
  - Various spatial data-structures
  - Various culling algorithms
  - Various geometric representations (polygonal, volume, parametric, etc.)
- Understand programmatic choices related to lighting and shading in real-time
  games, including understanding basic vocabulary, general computation and
  understanding of trade-offs of:
  - Various global illumination algorithms (i.e. shadow algorithms, ambient
    occlusion, etc.)
  - Various BRDFs and deferred shading
  - Related technologies, including texture mapping and framebuffers
- Understand programmatic choices related to animation in real-time games,
  including understanding basic vocabulary, general computation and understanding
  of trade-offs of:
  - Introductory physically-based modeling
  - Character animation (specifically skinned meshes)
- Be able to program a basic game with multiple moving components and
  interaction, shadow mapping, view frustum culling and two advanced graphics
  technologies from the provided list
- Write a large C++ real-time computer graphics application either as an individual
  or on a team and experience the joy of software engineering while working on a
  larger quarter long project.



## Assignments

- 1 pair program (5% of final grade)
  - OpenGL & C++ application
- 2 follow-on individual programs (vfc and shadow mapping – 5% each)
- One large team or individual final programming project (45% of final grade)
  - of your team’s choice (again using OpenGL and C++)
  - project must be approved by the instructor (see final project proposal &
rubric)
  - teams will be 1-6 people – see instructor for exceptions
  - all teams must meet in quarter deadlines (see syllabus for tentative
deadlines)
  - Note that individual assessment (grades) will be made via input from team
members for each milestone.
- 2 individual programming technologies (14% of final grade, 7% each)
  - OpenGL & C++ technologies integrated into group project
  - Code review required
- 2 mid-term exams (10% of final grade each)
- Final game play assessment (2% of final grade)
- Participation (4% of final grade)
  - attend class/ talk in class or office hours interaction

Please see the program description for deadline details.
There is a strict late policy for all assignments – no late programs/project demos will be accepted.



## Details

### Text

*Real-time rendering* Tomas Akenine-Moller and Eric Hanes (highly recommended)

Recommended:

- Any good modern graphics OpenGL reference, (e.g. *Foundations of 3D Computer Graphics* by S. Gortler)
- *Making Comics* and *Understanding Comics* by Scott McCloud

### Participation

Throughout the course, there will be many opportunities to participate interactively in and out of the classroom.
I expect you to participate by asking or answering questions, either in class or online on piazza.
To encourage in-class participation, laptops, phones, and other smart devices are not to be used during class, unless specified for workshop format classes.

### Honesty

Although I encourage you to have lively discussions with one another, **all work you hand in must be your own work**.
If your program or parts of your program are plagiarized from another student or unapproved sources including tutorials,
you will fail the course and a letter will be put in your file with Cal Poly Judicial Affairs.
Note some old tutorials do not use modern graphics – if you use them, this can result in problems.
You can talk to one another about your solutions and you may look at another student’s code that has a bug
(I encourage you to help each other with de-bugging), but you cannot look at someone else’s working code.

Note that I expect your OpenGL code to conform to at least OpenGL 3.0 standards (sometimes referred to as "modern graphics")
some specifics include no use of immediate mode for rendering and no OpenGL matrix stack calls (instead use `glm`)
and all shading will be computed using GLSL shaders.

The schedule on the home page of the website for the lectures and assignments may change
and is provided to give you a rough outline of the topics we will cover and the timings of your final project reviews.
Check reading chapters with the topic in case your book edition varies.
