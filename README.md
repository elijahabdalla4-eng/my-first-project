\# My First GitHub Project



This is my first GitHub repository.



I am learning how to use Git and GitHub to manage my projects.



Created by: Elijah Abdalla


Figure 1: Successfully created GitHub repository showing the README.md file and first commit.
1. Introduction
This user manual explains how to create a GitHub repository, clone it to a local computer, make changes to a project file, and upload those changes to GitHub using Git and PowerShell.
The procedure is designed for beginner computing students who want to learn how to manage and store their projects online.

2. Prerequisites
Before starting this procedure, the user needs:
A computer running Windows.
A stable internet connection.
An active GitHub account.
Git installed on the computer.
Windows PowerShell.
A web browser such as Google Chrome.
Basic computer knowledge.
3. Step-by-Step Procedure
Follow the steps below to create a GitHub repository and make your first commit.
Step 1: Open GitHub.
Action: Open a web browser and visit https://github.com/.
Expected result: The GitHub homepage appears.
Step 2: Sign in to GitHub.
Action: Enter your GitHub login details.
Expected result: Your GitHub dashboard appears.
Step 3: Start creating a repository.
Action: Select New repository from the + menu.
Expected result: The repository creation page appears.
Step 4: Enter repository details.
Action: Enter my-first-project as the repository name and select Public visibility.
Expected result: The repository details are displayed in the creation form.
Step 5: Create the repository.
Action: Click Create repository.
Expected result: GitHub displays your newly created repository.
Step 6: Open PowerShell.
Action: Open Windows PowerShell from the Start menu.
Expected result: A PowerShell terminal window appears.
Step 7: Navigate to the user directory.
Action: Enter cd $HOME in PowerShell.
Expected result: The terminal changes to the user's home directory.
Step 8: Clone the GitHub repository.
Action: Enter git clone https://github.com/elijahabdalla4-eng/my-first-project.git.
Expected result: Git downloads the repository files to the computer.
Step 9: Open the project folder.
Action: Enter cd my-first-project.
Expected result: The terminal location changes to the my-first-project folder.
Step 10: Display the project files.
Action: Enter ls in PowerShell.
Expected result: The README.md file appears in the list of project files.
Step 11: Open the README file.
Action: Enter notepad README.md.
Expected result: The README.md file opens in Notepad for editing.
Step 12: Edit the README file.
Action: Enter the project information into README.md and save the file.
Expected result: The README file contains the updated project information.
Step 13: Check the repository status.
Action: Enter git status in PowerShell.
Expected result: Git displays README.md as a modified file.
Step 14: Stage the changes.
Action: Enter git add README.md.
Expected result: The README file is added to the Git staging area.
Step 15: Commit the changes.
Action: Enter git commit -m "Update README with project information".
Expected result: Git creates a commit containing the updated README file.
Step 16: Upload the changes to GitHub.
Action: Enter git push origin main.
Expected result: Git uploads the committed changes to the main branch on GitHub.
Step 17: Verify the uploaded changes.
Action: Open the GitHub repository in a web browser and refresh the page.
Expected result: The updated README.md file and latest commit message appear in the repository.
4. Screenshot Descriptions
The following screenshots should be included to help readers understand the procedure and verify successful completion.
Screenshot 1: GitHub Repository Creation
This screenshot shows the GitHub repository named my-first-project, its Public visibility, and the repository creation page.
Screenshot 2: Successful Repository Cloning
This screenshot shows Windows PowerShell displaying the successful execution of the git clone command.
Screenshot 3: Successful Git Commit
This screenshot shows PowerShell displaying the commit message and confirming that the README.md file was successfully committed.
Screenshot 4: Successful Git Push
This screenshot shows PowerShell displaying the successful execution of git push origin main.
Screenshot 5: Final GitHub Repository
This screenshot shows the completed GitHub repository with the README.md file, project description, and latest commit message.
5. Troubleshooting
Common Error: Git Command Not Recognized
Problem: PowerShell displays an error stating that git is not recognized as a command.
Cause: Git may not be installed on the computer or may not have been added to the system PATH.
Solution:
Download Git from https://git-scm.com/downloads.
Install Git using the recommended installation settings.
Close and reopen PowerShell.
Run git --version to verify the installation.
Expected result: PowerShell displays the installed Git version, confirming that Git is ready to use.



API Documentation: Create a New Task
1. Overview
The Create Task API allows an authenticated user to create a new task within a project management application.
The API accepts task information such as the task title, description, assignee, due date, and priority level. After validating the submitted information, the system saves the task and returns its details to the user.
2. Endpoint Information
API Name: Create Task
HTTP Method: POST
Endpoint Path: /api/v1/projects/{projectId}/tasks
Authentication: Required
Content-Type: application/json
Success Status Code: 201 Created

3. Request Parameters
A. Path Parameters
The endpoint requires the following path parameter:


Parameter 
Datatype 
Required 
Description 
Projectld
Intejer
Yes 
Unique Id of the project where the task will be created.

B. Query Parameters
This endpoint does not require any query parameters. All task information is provided in the request body.
C. Request Body Parameters
The API accepts the following information in JSON format:

Parameter 
Data type 
Required 
Description
Tittle 
string
yes
Name of task
Description
string
no
Additional details about the task
AssigneeId
integer
yes
Id of the user assigned to the task
Duedate
string
yes
Task deadline in YYYY-MM-DD format
Priority
string
yes
Task priority:low,medium or high


4. Required Request Headers
The API requires the following HTTP headers:
Header
Required
Description
Authorization
Yes
Contains the user's access token using Bearer authentication.
Content-Type
Yes
Specifies that the request body contains JSON data.
Accept
Yes
Specifies that the client expects a JSON response.

Example:
Authorization: Bearer YOUR_ACCESS_TOKEN
Content-Type: application/json
Accept: application/json


5. Example API Request
The following example shows how a user can send a request to create a new task.
HTTP Method: POST
Endpoint:
/api/v1/projects/101/tasks
Request Headers:
Authorization: Bearer YOUR_ACCESS_TOKEN
Content-Type: application/json
Accept: application/json
Request Body:

{
  "title": "Complete Website Design",
  "description": "Design the homepage and contact page for the company website.",
  "assigneeId": 25,
  "dueDate": "2026-12-15",
  "priority": "high"
}



6. Successful API Response
HTTP Status Code: 201 Created
The server returns this response when the task has been successfully created.
Example Response Body:


{
  "success": true,
  "message": "Task created successfully.",
  "data": {
    "id": 501,
    "projectId": 101,
    "title": "Complete Website Design",
    "description": "Design the homepage and contact page for the company website.",
    "assigneeId": 25,
    "dueDate": "2026-12-15",
    "priority": "high",
    "status": "pending",
    "createdAt": "2026-11-10T07:00:00Z",
    "updatedAt": "2026-11-10T07:00:00Z"
  }
}

7. HTTP Response Codes
The API may return the following HTTP status codes depending on the result of the request.
Status Code
Name
Explanation
201
Created
The task was successfully created.
400
Bad Request
The request contains invalid JSON or malformed data.
401
Unauthorized
The user has not provided a valid authentication token.
403
Forbidden
The user does not have permission to create tasks in the project.
404
Not Found
The specified project or assignee does not exist.
409
Conflict
The request conflicts with an existing resource or project restriction.
415
Unsupported Media Type
The request does not use the supported JSON content type.
422
Unprocessable Entity
The submitted information fails validation.
429
Too Many Requests
The user has exceeded the allowed number of API requests.
500
Internal Server Error
An unexpected error occurred on the server.


8. Validation Rules
The API checks the following rules before creating a task:
The task title must not be empty.
The description is optional.
The assignee ID must belong to an existing user.
The due date must follow the YYYY-MM-DD format.
The priority must be low, medium, or high.
The specified project must exist.
The authenticated user must have permission to create tasks in the project.
If the submitted information does not meet these requirements, the API returns an appropriate error response.

9. Conclusion
The Create Task API provides a simple and structured way for authenticated users to create tasks within a project management application.
It uses the POST HTTP method, accepts JSON request data, validates the submitted information, and returns a response containing the newly created task.
This documentation helps developers understand how to use the endpoint correctly and handle possible responses.

