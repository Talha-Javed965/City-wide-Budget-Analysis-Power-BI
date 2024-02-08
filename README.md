Create a Power BI report that visualizes city-wide budgets and actuals. Find out which departments are generating the most revenue or spending the most money, and which departments have gone furthest over their budgets.
Techniques you’ll need to use:
Duplicate queries and merge queries
Hierarchies & Drill down
Tips:
Note how the transactions are divided between Expenditures and Revenues using the 14th column. Use this column to write measures in DAX that distinguish between revenue and expenditures (similar to how we differentiated between income and expenses in the Week 3 exercises).
Use the hierarchies functionality to create and analyze hierarchies in this data:
Hierarchy #1
Business Area (parent)
Fund Center (child)
Hierarchy #2
Category (parent)
Account (child)
Use the drill 
up/drill down functionality to navigate through the different hierarchi
Solutions
This dataset contains accounting data. Each transaction belongs to a fund, business area, fund center, account, and category. These attributes are how data is typically represented inside of the operating ledger of a business or government agency.
There are two general approaches for completing this week's exercise:

In the first approach, you can transform each of these attributes into its own table using the Duplicate Queries functionality in Power Query, remove all columns except the ones pertaining to each attribute, then remove duplicate values. When removing duplicates, you want to find the column that has the most unique values, then right-click and select "Remove Duplicates." You would then use the Merge Queries functionality in your original table to merge each attribute's ID column back into the main table. This approach helps to normalize the data, cutting down on duplicates and allowing for faster and more efficient filtering of the data within Power BI.

You can download a Power BI template showing the first approach here. The screenshot below shows the proposed data model.

Week 3 approach 1 data model

The second approach is my preferred approach. In the second approach, instead of transforming each attribute into a separate table, you will instead group the attributes that go together. For example, Business Area and Fund Center would go into one table together, and the GL Account and GL Category columns would go into a different table together. This is because these columns all naturally relate to each other, which you can determine by a close analysis of the data. In this approach, you will still use Duplicate Queries to break the data out into different tables, and you'll use Remove Duplicates and Merge Queries to bring everything back together in the main table. The main difference is that you will have fewer tables than before, which means fewer table relationships, resulting in a more efficient data model. Consider using Index Columns to create a primary key on each table, and bring those into the main table ("Budget vs Actuals") to create the table relationships.

Another benefit of this approach is you can create explicit hierarchies. For example, right-click on Business Area Name and select "Create Hierarchy" to create the new hierarchy, then drag "Fund Center Name" on top of the new hierarchy. Then you can use the hierarchy in your charts and tables. Here's a video from Patrick LeBlanc at "Guy in a Cube" on how to create hierarchies.

You can download a Power BI template showing the second approach here. 
![P-1](https://github.com/Talha-Javed965/City-wide-Budget-Analysis-Power-BI/assets/83302927/59241f47-efba-43bb-8f42-506d1b1d78ab)
![P-2](https://github.com/Talha-Javed965/City-wide-Budget-Analysis-Power-BI/assets/83302927/d4dc3340-286b-4ff2-9082-56f13687d821)
![P-3](https://github.com/Talha-Javed965/City-wide-Budget-Analysis-Power-BI/assets/83302927/7a6f5909-7d30-4206-9607-a01254afbe91)

