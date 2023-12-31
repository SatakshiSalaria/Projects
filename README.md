Project Logistics

The project features three stages, each being one sprint: 
1. Extract the user-level aggregated dataset using SQL.
2. Analyze the A/B test results using statistical methods in spreadsheets and visualizations in Tableau.
3. Create a written report of the A/B test results and optionally record a video presentation.

Project Background

Motivation
An A/B test is an experimentation technique used by businesses to compare two versions of a webpage, advertisement, or product feature to determine which one performs better. By randomly assigning customers or users to either the A or B version, the business can determine which version is more effective at achieving a particular goal.
You are a Data Analyst for an e-commerce company called GloBox. GloBox is an online marketplace that specializes in sourcing unique and high-quality products from around the world.
We believe that shopping should be an adventure, and we want to bring the world to your doorstep. From exotic spices and rare teas to handmade jewelry and textiles, we have a curated selection of products that you won't find anywhere else.
GloBox is primarily known amongst its customer base for boutique fashion items and high-end decor products. However, their food and drink offerings have grown tremendously in the last few months, and the company wants to bring awareness to this product category to increase revenue.

A/B Test Setup
The Growth team decides to run an A/B test that highlights key products in the food and drink category as a banner at the top of the website. The control group does not see the banner, and the test group sees it.

The setup of the A/B test is as follows:
1. The experiment is only being run on the mobile website.
2. A user visits the GloBox main page and is randomly assigned to either the control or test group. This is the join date for the user.
3. The page loads the banner if the user is assigned to the test group, and does not load the banner if the user is assigned to the control group.
4. The user subsequently may or may not purchase products from the website. It could be on the same day they join the experiment, or days later. If they do make one or more purchases, this is considered a “conversion”.

You can find a description of each table and its columns below.

1.) users: user demographic information
    id: the user ID
    country: ISO 3166 alpha-3 country code
    gender: the user's gender (M = male, F = female, O = other)

2.) groups: user A/B test group assignment
    uid: the user ID
    group: the user’s test group
    join_dt: the date the user joined the test (visited the page)
    device: the device the user visited the page on (I = iOS, A = android)

3.) activity: user purchase activity, containing 1 row per day that a user made a purchase
    uid: the user ID
    dt: date of purchase activity
    device: the device type the user purchased on (I = iOS, A = android)
    spent: the purchase amount in USD

File for reference:
1.) Tableau link :https://public.tableau.com/app/profile/satakshi.salaria7665/viz/GloBoxProject_16888494285040/TestGroupResults#1
2.) speadsheet link:https://docs.google.com/spreadsheets/d/1Dpf4TRPjq_pHtsODAoondvYVN0ExF334Ntqrj0G3z-c/edit#gid=1235041860
