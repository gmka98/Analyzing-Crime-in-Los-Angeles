# 🔍 LAPD Crime Data Analysis – Los Angeles, California 😎

## 📘 Project Overview

This project analyzes crime data provided by the Los Angeles Police Department (LAPD) to identify patterns in criminal activity. Los Angeles, known for its sunshine and celebrity glamour, also faces the realities of crime that come with being a large metropolitan area. 

The goal is to extract insights from real crime data to help inform and optimize resource allocation for law enforcement. This analysis focuses on understanding crime trends based on **hour of occurrence**, **geographical area**, and **victim age**.

The data used is a modified version of the original [Los Angeles Open Data Crime Dataset](https://data.lacity.org/), provided in `crimes.csv`.

---

## 📂 Dataset Description

The dataset includes crime reports and contains the following key columns:

| Column         | Description                                                                 |
|----------------|-----------------------------------------------------------------------------|
| `DR_NO`        | Official LAPD file number                                                   |
| `Date Rptd`    | Date crime was reported                                                     |
| `DATE OCC`     | Date crime occurred                                                         |
| `TIME OCC`     | Time crime occurred (24-hour format)                                        |
| `AREA NAME`    | Geographic patrol area name                                                 |
| `Crm Cd Desc`  | Description of the crime                                                    |
| `Vict Age`     | Victim's age                                                                |
| `Vict Sex`     | Victim's gender (M/F/X)                                                     |
| `Vict Descent` | Victim's ethnic descent                                                     |
| `Weapon Desc`  | Weapon used (if applicable)                                                 |
| `Status Desc`  | Status of the investigation                                                 |
| `LOCATION`     | Street location of the crime                                                |

---

## 🧪 What I Did

### ✅ Data Cleaning
- Loaded the dataset using `pandas`
- Filtered out invalid or negative victim ages
- Converted crime time to extract the hour (`HOUR OCC`)

### ✅ Exploratory Data Analysis (EDA)
1. **Peak Crime Hour**
   - Extracted hour from `TIME OCC`
   - Used `sns.countplot` to visualize crime frequency by hour
   - Identified the hour with the most crimes and saved it as `peak_crime_hour`

2. **Night Crime Hotspot**
   - Defined *night hours* as 10:00 PM to 3:59 AM (22, 23, 0, 1, 2, 3, 4)
   - Filtered the dataset for these hours
   - Grouped by `AREA NAME` and identified the area with the most night crimes
   - Saved the result as `peak_night_crime_location`

3. **Crimes by Victim Age Group**
   - Defined age brackets:
     - `"0-17"`, `"18-25"`, `"26-34"`, `"35-44"`, `"45-54"`, `"55-64"`, `"65+"`
   - Used `pd.cut` to bin victim ages
   - Counted number of crimes per age group and saved as a `Series` named `victim_ages`

---

## 🧾 Key Results

```python
peak_crime_hour = 20  # for example
peak_night_crime_location = "77th Street"  # for example

# Victim age distribution (example)
victim_ages = pd.Series({
    "0-17": 1023,
    "18-25": 3452,
    "26-34": 4031,
    "35-44": 3567,
    "45-54": 2890,
    "55-64": 1723,
    "65+": 990
})
