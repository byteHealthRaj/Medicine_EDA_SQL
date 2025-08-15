
--MEDICINE EXPLORATORY DATA ANALYSIS PROJECT(ENTRY LEVEL)

--View Top 10 Medicines 
Select top 10 name
from medicine_dataset

--View Top 5 Manufacturers
Select Top 5 Manufacturer
from medicine_dataset

--What are the total Number of Medicines Manufactured
SELECT COUNT(*) AS total_medicines FROM medicine_dataset;

--What are the Unique Categories of meidcines
SELECT DISTINCT Category FROM medicine_dataset;

--How many are the MAnufacturers of Those Medicines
SELECT COUNT(DISTINCT Manufacturer) AS unique_manufacturers FROM medicine_dataset;

--DATA DISTRIBUTION
--What are the most common medicine categories
SELECT Category, COUNT(*) AS total_medicines
FROM medicine_dataset
GROUP BY Category
ORDER BY total_medicines DESC;

--What are the 5 Dosage Forms
SELECT Top 5 Dosage_Form, COUNT(*) AS count
FROM medicine_dataset
GROUP BY Dosage_Form
ORDER BY count DESC

--Find top 5 manufacturers by number of medicines produced

SELECT top 5 Manufacturer, COUNT(*) AS total_products
FROM medicine_dataset
GROUP BY Manufacturer
ORDER BY total_products DESC

-- Strength and Dosage Analysis

--What is the highest medicine strength
SELECT top 1 Name, Strength
FROM medicine_dataset
ORDER BY CAST(REPLACE(Strength, ' mg', '') AS INT) DESC

--What is the average strength of medicines
SELECT Category, AVG(CAST(REPLACE(Strength, ' mg', '') AS INT)) AS avg_strength
FROM medicine_dataset
GROUP BY Category
ORDER BY avg_strength DESC;

--How many drugs are there in terms of classification
SELECT Classification, COUNT(*) AS total
FROM medicine_dataset
GROUP BY Classification;

--What is the most common indication per classification
SELECT Classification, Indication, COUNT(*) AS frequency
FROM medicine_dataset
GROUP BY Classification, Indication
ORDER BY frequency DESC;

--Top 5 Manufacuterer for prescription medicines

SELECT Top 5 Manufacturer, COUNT(*) AS total_prescription
FROM medicine_dataset
WHERE Classification = 'Prescription'
GROUP BY Manufacturer
ORDER BY total_prescription DESC

--What are the most common dosage form for all categories

SELECT Category, Dosage_Form, COUNT(*) AS frequency
FROM medicine_dataset
/** for according to different category
where category = 'Antibiotic'
*/
GROUP BY Category, Dosage_Form
ORDER BY Category, frequency DESC;

--To find missing Data/Blank Data

SELECT *
FROM medicine_dataset
WHERE Name IS NULL 
   OR Category IS NULL
   OR Dosage_Form IS NULL
   OR Strength IS NULL;











