# Ecommerce-dashboard

## Table of content

  - [Project Overview](#project-overview)
  - [Data Sources](#data-sources)
  - [Tools used/steps followed](#tools-used-and-steps-followed)
  - [DAX used](#dax-used)

## Project Overview

This data analysis project aims to provide insights into the sales performance of Ecommerce company over the past year. By analyzing various aspects of the sales data, we seek to identify trends, make data-driven recommendations, and gain a deeper understanding of the company's performance.


![Screenshot 2024-12-22 160926](https://github.com/user-attachments/assets/0eff42ff-1b6c-43ce-b7af-94769df12dcf)




### Data Sources


Sales Data: The primary dataset used for this analysis is the "Sales overview data.csv" file, containing detailed information about each sale made by the company.

### Tools used and steps followed

- Excel - Data Cleaning [Download here](https://microsoft.com)
- PowerBI - Creating reports

🪜𝗦𝘁𝗲𝗽 𝗳𝗼𝗹𝗹𝗼𝘄𝗲𝗱 𝘁𝗼 𝗰𝗿𝗲𝗮𝘁𝗲 𝗿𝗲𝗽𝗼𝗿𝘁:

Import Data : Gathered data from team leads and seamlessly imported it into Power BI for easy access.

📑Data Cleaning:
using power query and power query editor to clean the data like removing null values, remove unnecessary duplicates, change Data types.

📊Data Implementation: used 𝗗𝗔𝗫 function to calculate and adding new measures

🤗I used different types of customized visualization 💻(Area 𝗰𝗵𝗮𝗿𝘁, 𝗦𝘁𝗮𝗰𝗸𝗲𝗱 𝗯𝗮𝗿 𝗰𝗵𝗮𝗿𝘁, 𝗠𝗮𝗽 𝗩𝗶𝘀𝘂𝗮𝗹, Donut 𝗰𝗵𝗮𝗿𝘁 , 𝗠𝗮𝘁𝗿𝗶𝘅 & 𝗦𝗹𝗶𝗰𝗲𝗿 )⌨🖱

### DAX used

#Below DAX formulas created ofr each KPI

#KPI's Requirements

Central Region:
- Display Sales, Profit, and Quantity as per the selected year filter.
- Allow dynamic selection between Sales, Profit, and Quantity.
- Show Sales for the previous year based on the selected year.
- Create a bar sparkline for monthly data, including an average line for better trend analysis.

```KPI
Parameter metric for= total sales, profit ,quantity

PY profit =
     var selected_value= SELECTEDVALUE('Calender table'[Year])
     VAR PY= CALCULATE([Total Sales],'Calender table'[Year]=selected_value-1)
     VAR formatpy=FORMAT(PY/1000,"0.00")
     RETURN
          IF(ISBLANK(PY),"NO DATA","PY Sales:" & formatpy )

```

```
1)CYsales = CALCULATE(SUM('Sales Data'[Sales]),DATESYTD('Calender table'[Date]))

2)PY sales =
 VAR selectedYear=SELECTEDVALUE('Calender table'[Year])
 VAR PYsales=CALCULATE([Total Sales],'Calender table'[Year]=selectedYear -1)
 VAR formatpysales=FORMAT(PYsales/1000,"0.00")
 return
        if(ISBLANK(PYsales),"NO DATA","PY Sales:" & formatpysales)

3)YOY Sales =
  VAR yoy= ([Total Sales]-[PYsales])/[PYsales]
  VAR symbolicon=IF(yoy>0,UNICHAR(9650) & " " &FORMAT(yoy,"0%"),UNICHAR(9660) & " " & FORMAT(yoy,"0%"))
  return symbolicon

```


![Screenshot 2024-12-22 161938](https://github.com/user-attachments/assets/adb444bc-e273-49d6-be48-a4c310519240)
