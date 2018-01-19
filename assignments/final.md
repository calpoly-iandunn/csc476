---
layout: page
active: assignments
title: "Final Project"
auto-title: true
---



Your primary project for this course consists of a quarter long project to be completed in ~9 weeks.
This is your chance to make a portfolio quality game/virtual environment.
**This project is worth 45% of your final grade in this class (plus 20% for individual technologies + 2% final game play) = 67% of your grade in this class).**



## Marketplace

We will hold a "game market place" to establish teams and final projects.
This marketplace is a chance for potential managers or team members to "pitch" their game idea(s) to the class and try to form teams.
Ideally, teams of size 4 are formed.
All games must meet the required technical requirements.

<a href="https://drive.google.com/file/d/1szFqFMXgwGhsneo5m6VzIMx0QfGI-YPM/view?usp=sharing" class="btn btn-info">Example Pitches</a>



## Requirements

All games must be or include (whole team equally responsible for):

- At least one single **level** complete game or interactive 3D **world** with nice graphics that contains enough variation from other team's projects
  (see below for details for specific graphics technologies).

- It must be **fun** and enjoyable to interact with (i.e. winnable game or compelling interactive world).
  You will be assessed on this metric via play-testing by the class and feedback from the instructor.

- Some kind of **audio**.

- Good **software development** (this is vague, but consider the value of careful design, unit testing, writing clear code and general performance issues).
  Mostly, poor software design and or version control is not an excuse to not meet a deadline or not de-bug a feature.

In addition, the project must include both **Major Technologies** and **Additional Technologies**.

You are required to individually take responsibility for two technologies
(at least one of them being from the 'major' technologies list).
To get credit for these technologies,
you must review your individual code with the instructor in person.

20% of your final grade will be evaluated based on your individual creation of these graphics technologies and the associated code review.


### Major Technologies

The project must include the following graphics technologies (or instructor approved substitution).
One person on the team needs to choose to be responsible for one of the following major technologies,
and **ALL** major technologies must be present in all games:

  - A camera/view that changes: the camera must be mostly free to move with a player in the 3D world, 2.5D camera is allowed but it *must rotate*, not always face in a single specific direction.

  - A nice complex environment with characters that navigate and interact with that environment, with articulated character motion.

  - Some form of collision detection and response using a spatial data-structure
    (i.e. bounding sphere hierarchy, uniform spatial subdivision, etc.) - note however some hierarchy required for view frustum culling

  - Shadows: shadow maps or shadow volumes

  - Hierarchical view frustum culling or appropriate occlusion culling (pending instructor approval)

  - Two specialized rendering techniques from:
    - physically based rendering (PBR) pipeline
    - deferred shading
    - normal mapping
    - environment mapping
    - non-photo-realistic rendering (NPR)
    - screen-space ambient occlusion
    - or instructor approved substitute


### Additional Technologies

Now, depending on your team size, choose 2-6 of the below technologies,
(choose as many as needed such that each team member is responsible for at least 1 major technology and 1 other technology, major or additional).

All technologies must have a demonstrable visual side-effect.

- level creation tool
- mesh simplification tool
- sophisticated HUD
- management of level-of-detail modeling, either terrain or character models
- complex pathing (and/or splines) for characters
- grab bag of shading: <exact shaders must be approved by instructor>
    - über shader and 2 different shading models (BRDFs) or
    - bloom and motion blur (or depth-of-field)
- grab bag of game effect <exact effects must be approved by instructor>
    - particle system
    - lens flair
    - interesting fog
    - billboarding, etc.
- complex collision response, (scripted) fracturing, complex alpha mapping, etc.
- some bonus feature (graphics or otherwise)\*


**\*Note** that the above list of technologies does not include a lot of features common in many games (i.e. AI or networking for example)
you are welcome to build in these features but they do not supersede/replace any of the graphics requirements.
They can, however, count for your bonus feature.
In addition, nice assets (i.e. characters, textures, environments, etc.) are important to the look and feel of many games
but creating or importing them do not count towards any of the graphics requirements but can be applied as your bonus feature.


### One Cool Thing

Your project will need to be a fairly complete single level game, however,
I encourage your team should focus energy on **one cool thing** that will make your game stand out.
This might be a very rich visual environment or particularly cool character movement/interaction,
or a visually exciting effect, or a very particular look/feel to the game, etc.
Again, you need to include all the features specified, but focusing your effort on one very nice aspect of the game is a good way to make a simple game stand out.



## Details

### Teams

Each team will pick a **manager** and it is assumed that team participants will specialize.
Every member of the team must take responsibility for one major graphics technology and either a second major graphic technology or one of the optional technologies.
Managers and teammates will help decide grade distribution within the team (see below) and will be held responsible for getting their team to meet deadlines
(i.e. the manager will be my point person of harassment).
Part of each of your grades depends on your mutual assessment of one another.


### Outside Code

*A note about using outside references and technology/code:*
You are welcome to use any outside resource/code/technology that will help your team meet its goals
(including assets, modeling programs, physics engines (not full collision), tutorials, audio libraries, etc.).

However, **all** of the required graphics technology must be implemented by one of your team members in a way that does not take advantage of other classmates
(i.e. you copying code from a tutorial for view frustum culling **is** taking unfair advantage of your classmates).

You or some member of your team must understand/master all of the required graphics technology required for your game.
In addition, you are required to list all references you plan to use in your final project proposal and in your project report.
Be very careful when considering the use of outside technology, sometimes it takes as long to learn someone else's code as it does to write it yourself.


### Progress Demos

**You and all your team members are required to be present** for 4 intermediary progress checks and the final demo of the project.
**These demos are mandatory and will be graded.**
At each demo, a portion of your grade will be awarded (i.e. the same portion of the project that should be done.
In other words 25% of your grade for your final project will be assessed at the 25% check-in).
If you miss a check off, you will automatically loose that portion of your final project grade.
These check-offs will happen in lab - see the course schedule or calendar for dates.

- **25%**  (First 25% of grade assessed)
- **50%**  (Additional 25% of grade assessed)
- **75%**   (Additional 25% of grade assessed)
- **90%**  (Additional 15% of grade assessed + game play assessment conducted this session)
- **100% done and demoed to entire class on 3/21** (final 10% of final project grade assessed - it is expected that you will take into account the feedback given at the playtest session)

Note that for grading, I will assign each team a grade at the check-in.
**That grade can then be scaled based on feedback from both the manager and the team members.**
Your team grade counts toward 45% of your course grade, your individual technology grade is 20% of your final course grade



### Playability Testing – 90% assessment:

Note that in addition to the 45% of your final grade for your team’s game, which will be evaluated throughout the quarter for your final project, we will have some in class playability testing, during the 90% assessment time period.  This will be a chance for 5 members of the class not on your team to play your game.  Your team will need to have your game installed and ready to play by others in the class.  A strict rubric for grading one another’s games will be provided and you will grade one another’s game.  This playability assessment, (assuming all issues that can be addressed will be), will account for 2% of your final grade.


## Grading

- **No late programs** will be accepted.
- Your final grade will be the culmination of your demos throughout the quarter as specified earlier in this document.


### Source Code Hosting

Use of GitHub Classroom is optional for this assignment,
but is an easy way to set up a private repository shared between team members.

<a href="https://classroom.github.com/g/HU0_GOIm" class="btn btn-info">GitHub Classroom</a>

However, your project *must be hosted in a distributed version control system*.
Git is the obvious choice.
I do not have to have access to this source code repository,
but it must exist.

