# Title
DE101 Bootcamp- Code Review Week 12

# Name
Nikisha Banks

# Technologies Used: 
Git hub, Visual Studio Code, Airflow, Docker

# Languages and tools used: 
DAG Python and Bash Operators

# Description:
In this project, Airflow was used to orchestrate a workflow that did the following:
  1.Create a DAG (Directed Acyclic Graph) that uses a file sensor to check if a file has been uploaded to a folder named "data"
  2.Create a task that reads each row in the file and checks to see if the values in each row match values in a given list. If there is a match, the task adds the item to a new list
  3.Create a task that uses a Python function that takes the new list as an argument and prints the item that has the most occurrences  

# Setup/Installation Requirements:
- To see the code files in this project:
  1. Clone the repo in Git Hub: 
                a. Click the green "code" button
                b. Under the "Local" tab, copy and paste the URL that is under HTTPS
- Set up Airflow 
  1. In your visual studio terminal of your choice, create and activate a virtual environment in your repository folder by typing the following commands: 
     1. python3.10 -m venv <virtual environment name>
     2. source <virtual environment name>/bin/activate 
  2. Run the setup.sh file by typing ./setup.sh. This script sets up your environment and installs the necessary components
  3. Create the following new directories in the same folder:
     1. ./logs
     2. ./plugins
     3. ./dags
  4. Pull down the latest version of Airflow by typing 	"curl -LfO 'https://airflow.apache.org/docs/apache-airflow/stable/docker-compose.yaml'"
  5. Create a Airflow user id by typing "echo -e "AIRFLOW_UID=$(id -u)\nAIRFLOW_GID=0" > .env"
  6. Start Airflow and all related containers by typing:
     1. docker-compose up airflow-init
     2. docker-compose up
  7. Leave that terminal running and then open a new terminal to continue working in
  8. In your browser, go to localhost:8080, this will take you to the Airflow Graphical User Interface
  9. In the Airflow User Interface (browser), create a file connection called "data_fs" by clicking "Admin" --> "Connections". Enter the following:
     1.  Connection ID = data_fs
     2.  Connection Type = file (path)
     3.  Path = {"path":"/data"} 
- Shutting down Airflow and docker
  1. Switch to the terminal that is running your Airflow commands
  2. Either press CTRL + C or type "docker compose down"
  3. Type "docker system prune --volumes" to remove all volumes from the docker container
  4. type "docker volume list" to confirm that there are no volumes
   
# Known Bugs
The following errors occurred while running the DAG in Airflow

![Image](https://github.com/nbanks062523/code_review_wk12/blob/1e5c521a2ec455adc3d7186542dde3d6b095fcbd/Week12_ErrorMsg1.png)

![Image](https://github.com/nbanks062523/code_review_wk12/blob/1e5c521a2ec455adc3d7186542dde3d6b095fcbd/Week12_ErrorMsg2.png)


# Project Visuals
## DAG 
The DAG Diagram in this project shows the order of tasks and their dependencies, if any
  1. The flow starts with the 'wait_for_file' task that creates a DAG that uses a File Sensor to check if the votes.csv file has been delivered to the "data" folder
  2. The second task is the 'Read_file_task', this task is a Python Operator task that will read each row in the votes csv file and check whether the value is in a given list called flavors_choices and appends it to a new list
  3. The third task is also a Python Operator task that takes the list from the previous task and prints the item that appears the most
     
![Image](https://github.com/nbanks062523/code_review_wk12/blob/e98d628a7965382230a8f601a5d8ec97f9bc17bf/Week12_DAGOutput.png)
---
## DAG Final Outcome
As shown in the image the DAG failed after 3 attempts. 

![Image](https://github.com/nbanks062523/code_review_wk12/blob/e98d628a7965382230a8f601a5d8ec97f9bc17bf/Week12_DAGOutput2.png)
---

# License
*Copyright 2024, Data Stack Academy Fall 2023 Cohort*

*Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the “Software”), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:*

*The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.*

*THE SOFTWARE IS PROVIDED “AS IS”, WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.*# code_review_wk12
# code_review_wk14
