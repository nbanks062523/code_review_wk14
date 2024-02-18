# Title
DE101 Bootcamp- Code Review Week 14

# Name
Nikisha Banks, Alex Wallace

# Technologies Used: 
Git hub, Visual Studio Code, Airflow, Docker, Google Big Query

# Languages and tools used: 
DAG Python Operators

# Description:
In this project, Airflow was used to orchestrate a workflow that did the following:
1.Create a DAG (Directed Acyclic Graph) that executed tasks to add CSV files to Google Cloud
    1.The DAG file begins with two functions that act as a checklist to ensure that the data files are properly placed and to ensure that the DAG is able to connect to the Big Query client
    2. A DAG is then created with it's accompanying tasks
    3. The first 2 tasks run the checklist functions, followed by an empty operator for branching the table creation tasks
    4. The next task runs a loop that loads each table
    5. Finally, another empty operator is used to bring the tasks back together 

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
no known bugs

# Project Visuals
## DAG 
The DAG Diagram in this project shows the order of tasks and their dependencies, if any.
---
## DAG Final Outcome
As shown in the image the DAG failed several times due to Google permission issues and finally succeeded on the 7th attempt  

![Image](https://github.com/nbanks062523/code_review_wk14/blob/6c5dea04c7b297e1933e6297a24483e99800f5a1/DAGFinalResults_Week14.png)

![Image](https://github.com/nbanks062523/code_review_wk14/blob/6c5dea04c7b297e1933e6297a24483e99800f5a1/DAG_graph_Final.png)
---
## Final Data Outcome
As shown in the images, the following tables were created by the DAG: 
  1.Food Inflation by month - A table that shows the inflation rates of food by month year over year
  2.Grocery Prices by month - A table that shows the price of groceries month over month by state
  3.SNAP Population, SNAP Poverty Population, SNAP Program Participants - These tables display data around the Supplemental Nutrition Assistance Program and its recipients over time by state    

![Image](https://github.com/nbanks062523/code_review_wk14/blob/6c5dea04c7b297e1933e6297a24483e99800f5a1/DataTables_Wk14.png)

![Image](https://github.com/nbanks062523/code_review_wk14/blob/6c5dea04c7b297e1933e6297a24483e99800f5a1/SampleData_FoodInflation.png)

![Image](https://github.com/nbanks062523/code_review_wk14/blob/6c5dea04c7b297e1933e6297a24483e99800f5a1/SampleData_GroceryPrices.png)

---
# License
*Copyright 2024, Data Stack Academy Fall 2023 Cohort*

*Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the “Software”), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:*

*The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.*

*THE SOFTWARE IS PROVIDED “AS IS”, WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.*# code_review_wk14
