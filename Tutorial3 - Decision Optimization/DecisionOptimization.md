# Use Decision Optimization  to optimize availability PPE equipment based on COVID-19 data for Michigan counties

## Tutorial
Decision Optimization adds prescriptive analytics capabilities to IBM Watson Studio and IBM Watson Machine Learning. This hands-on lab is created around a simple Marketing Campaign problem. In 45 minutes, you set up a Watson Studio project and go through all the necessary steps to use Decision Optimization for Watson Studio and Decision Optimization for Watson Machine Learning.

In the previous 2 Tutorials we used the COVID-19 dataset to refine and predict cases using SPSS visual model building interface.Based on predictive model counties and other data we will use prescriptive analytics (optimization) to figure out what PPE equipment Michigan counties and hospitals would need to be prepared.

An optimization model defined in terms of
 - an objective, decision variables, and constraints
 - a optimization engine to solve the model instance
 - data to create an instance of the model

The purpose of the optimization process is to find values for the decision variables to satisfy all constraints and optimize the objective function

As an example, an objective function could be to maximize profit or to minimize costs. In our use case it is maximize allocation of PPE products
The decision variables might represent how many of different types of product to allocate based on importance and county requirements
or which county to assign these products and how much.

And the constraints could be the availability restrictions, fairness in allocation.

Optimization-based decision applications involve embedded optimization models and algorithms as part of larger applications that might include,
for example, a graphical user interface and integration with databases and other enterprise
systems.Such applications can be used to perform "what-if" analysis,where users can compare different scenarios, each involving different data.
By invoking the optimization model interactively and repeatedly, users can judge the impact of data changes, and analyze trade-offs between conflicting business goals and constraints.

In this tutorial, you will explore the following key capabilities:
 * You will learn how to build Optimization model
 * A model builder to guide developers through the typical optimization development steps
 * Dashboards for communicating the optimization model results

Required software, access, and files
To complete this lab, you will need:
• IBM Cloud Pak for Data
. IBM Watson Machine Learning Service

Acknowledgements

I would like to acknowledge the following team members for providing guidance with various parts of these tutorial
Xavier Ceugniet
Alain Chabrier
Victor Terpstra

You will also need to download and unzip the files in [Part3](https://github.com/neravdoshi/DSBlog/tree/master/Part3)

## Step

1. [Add a Decision Optimization to your Watson Studio Project](#1-Add-a-decision-optimization-to-your-watson-studio-project)
2. [Import the data required to build the model](#2-import-the-data-required-to-build-the-model)
3. [Run models and analyze results](#3-run-model-and-analyze-results)

### 1. Add a Decision Optimization to your Watson Studio Project

* Click on your newly created project.

* Once you have created your Watson Studio Project, you see a blue `Add to Project` button on the top-right corner of your screen.

![addProj](../images/Tutorial3-Step1-newDOproject.png)

* Click on `Add to Project` and then select `Decision Optimization Experiments`.Select Watson Machine Learning service from the dropdown menu.Note: If Watson Machine Learning service is not available then create a service using Lite plan

![addProj](../images/Tutorial3-Step1-DOservice.png)
![addProj](../images/addWMLservice.png)

### 2. Import the data required to build the model
* Click the `Find and add data`. icon on the top right side and click on `browse`.as shown below
![importProj](../images/Tutorial3-Step2-find-and-add-data.png)

* Select all files and  Click `Open`. and import 5 input files required for building this model
![importProj](../images/Tutorial3-Step2-importdata-files.png)
Product.csv - This file contains product information. the columns in the file as follows
Product - name of the products
cost - cost to procure the products
qty_per_unit - number of product in 1 unit
unit_of_measure - metrics
importanceFactor - importance with respect to pandemic
required_qty_per_person - It is amount of product needed per patient/cases

ProductAvailability.csv - These file contains product that is available for entire state to be distributed to the counties.
Product - name of the products
Availability - Qty of units available for that time period



* Next, select `From File` and `browse` to where you cloned this repository. Select the `Base Scenario MI.zip` file. Next, click `Create`.

![importProj](../images/DOScenariofile.png)

* Click `Prepare data`. to look at tables that were imported. You can see product, plant, forecasted demand and market data along with other several tables.
![importProj](../images/MBpreparedata.png)

### 3. Run model and analyze results
* Click on `Run model` on model builder and then look at the optimization code written in python.Next is Click the `Run model`. This will pass the input data and python model to CPLEX engine to provide recommendation

![runProj](../images/MBRunmodel.png)

* Click on `Explore solution` on model builder and then look at the Objectives/KPI and Solutions tables link to review the output from optimization engine
![runmodel](../images/MBExploreKPI.png)

* Click `Visualization` to review the pre-populated dashboard.
![runmodel](../images/DOvisualization.png)
![runmodel](../images/DOsolution.png)
![runmodel](../images/DOproductionchart.png)

### Summary

This tutorial demonstrates a small example of creating a prescriptive optimization model on IBM Decision Optimization on Watson Studio(CPLEX engine). The tutorial goes over on importing the scenario into the project and running the model. The last step of the tutorial is about how to visualize and evaluate the results. You can see the total production required to meet demand. Based on cases you can allocate certain PPE equipemnt to counties that have high number of COVID cases.
