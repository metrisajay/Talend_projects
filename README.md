
I’ll be using the the [Insurance_dataset](https://www.kaggle.com/utkarshakathayat/insurance-dataset

I have used below 5 processing Talend components:
tLogRow
tMap
tFilterRow
tAggregateRow
tReplace

Replacing missing or null values
tmap component from the processing family. We’ll form expressions in the tMap component window using the available functions to transform data as per requirement.
row1.smoker.equals("NAN") ? "no" : row1.smoker
row1.region.isEmpty() ? "northeast" : row1.region
Relational.ISNULL(row1.bmi) ? 20.00 : row1.bmi

replacing missing and null values

Creating a column — Birth Year
the first parameter passed in the addDate function is another in-built function provided by Talend date category- getCurrentDate(), which as the name suggests returns the current date. We need to subtract the age so the second parameter passed is minus of age and third is yyyy since the year is required.
TalendDate.addDate(TalendDate.getCurrentDate(),-row1.age, "yyyy")

Categorical
tReplace component from the processing family which searches and replaces in the input columns defined and helps to clean the file before further processing.


Filtering and Aggregating Data
We will compare the average insurance charges for smoker and non-smoker males and females with children

a) We will filter out the family with children first , so we will apply the filter as children > 0

b)Once the filtered data is passed we will group the data by sex and smoker and apply the average function to the charges column

family having children and non smoker is having less insurance charges as compared to smoker


