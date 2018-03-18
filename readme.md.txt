I have been intersted in machine learning & Artificial Intelligence since College. And I have worked on some ML projects. However, this happens to be my first Kaggle Competition. And my first Jupyter notebook.

Oh, and my Python is a bit patchy, so please excuse any crudeness in the code.

The competion is hosted by DonorsChoose- a website where teachers can request resources for their students.
Link- https://www.kaggle.com/c/donorschoose-application-screening/

The aim of the contest is to help DonorsChoose volunteers to screen applications by predicting the probability of a project proposal geting approved.
The data set consists of one train file containing details of projects, one resource file containing details of resources requested in each project & a test file which is identical to the train except for the project_is_approved field, which is missing.

Fields in the train & test.csv:-
id - unique id of the project application
teacher_id - id of the teacher submitting the application
teacher_prefix - title of the teacher's name (Ms., Mr., etc.)
school_state - US state of the teacher's school
project_submitted_datetime - application submission timestamp
project_grade_category - school grade levels (PreK-2, 3-5, 6-8, and 9-12)
project_subject_categories - category of the project (e.g., "Music & The Arts")
project_subject_subcategories - sub-category of the project (e.g., "Visual Arts")
project_title - title of the project
project_essay_1 - first essay*
project_essay_2 - second essay*
project_essay_3 - third essay*
project_essay_4 - fourth essay*
project_resource_summary - summary of the resources needed for the project
teacher_number_of_previously_posted_projects - number of previously posted applications by the submitting teacher
project_is_approved - whether DonorsChoose proposal was accepted (0="rejected", 1="accepted"); train.csv only 

My attempts made till date:-

>JupyterNotebookDonorsChoose1 -> simple decision tree classifier . Works on the school_state, project_grade_category, project_subject_categories, project_subject_subcategories & teacher_number_of_previously_posted_projects.

Got a public score of .50943, which is somewhat expected for such a simple model.

Feature importances:-

0.37 for state, 0.11 for grade category, 0.087 for project category, 0.20 for project subcategory & 0.2257 for teacher_number_of_previously_posted_projects.

> JupyterNotebookDonorsChoose1.1 -> also simple decision tree. Same input feature set.
But small tweaks (Entropy gain instead of Gini measure, split only when >=5 samples at a node etc.)

Marginal improvement- public score of 0.51405.

> JupyterNotebookDonorsChoose2 -> basic random forest . Same input feature set.

Marginal improvement- public score of 0.51695.

Tweaked parameters:- number of trees=500, criteria= entropy, max depth=3, warm start =true

Sizable increase to 0.58502 (32 places up the leaderboard).

> JupyterNotebookDonorsChoose3-> basic xgboost with 500 trees.

Score= 0.57600



BTW, I used an Azure Linux Data Science VM for this, & I must say, it seems pretty sweet. All the bells & whistles are pre-installed. No setup required. (Disclaimer: I currently work for Microsoft)