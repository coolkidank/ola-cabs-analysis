# ola-cabs-analysis
Ola Analysis involves a detailed examination of Ola Cabs, a leading ride-hailing service, to uncover insights into its operational efficiency, market performance, customer behavior, and strategic positioning. By performing this analysis, stakeholders can identify areas for improvement, forecast future performance, and make data-driven decisions to enhance Ola's competitive edge and profitability.

Queries For Ola Analysis:

Create Database Ola;

use Ola;

-- 1. Retrieve all successful bookings:

CREATE VIEW Successful_Booking AS

SELECT *

FROM bookings

WHERE booking_status = "Success";


-- 2. Find the average ride distance for each vehicle type:

SELECT Vehicle_Type, ROUND(AVG(Ride_Distance),2) AS Avg_Distance

FROM bookings

GROUP BY Vehicle_Type;


-- 3. Get the total number of canceled rides by customers:

SELECT COUNT(*) AS Cancelled_By_Customers

FROM bookings

WHERE booking_status = "Canceled by Customer";


-- 4. List the top 5 customers who successfully booked the highest number of rides:

SELECT Customer_ID, COUNT(booking_ID) AS Highest_Number_Of_Rides

FROM bookings

WHERE booking_status = "Success"

GROUP BY Customer_ID

ORDER BY Highest_Number_Of_Rides DESC

LIMIT 5;



-- 5. Get the number of rides canceled by drivers due to personal and car-related issues:

SELECT COUNT(*) AS Cancelled_By_Driver

FROM bookings

WHERE Canceled_Rides_by_Driver = "Personal & Car related issue";


-- 6. Find the maximum and minimum driver ratings for Prime Sedan bookings:

SELECT MAX(Driver_Ratings) AS Max_Rating, MIN(Driver_Ratings) AS Min_Rating

FROM bookings

WHERE Vehicle_Type = "Prime Sedan";


-- 7. Retrieve all rides where payment was made using UPI:

SELECT *

FROM bookings

WHERE Payment_Method = "UPI";


-- 8. Find the average customer rating per vehicle type:

SELECT Vehicle_Type, ROUND(AVG(Customer_Rating), 2) AS Avg_Customer_Rating, 

COUNT(Vehicle_Type) AS Number_of_Vehicles
    
FROM bookings

GROUP BY Vehicle_Type;


-- 9. Calculate the total booking value of rides completed successfully:

SELECT SUM(Booking_Value) AS Total_Successfull_Booking

FROM bookings

WHERE booking_status = "Success";


-- 10. List all incomplete rides along with the reason:

SELECT Customer_ID, Incomplete_Rides, Incomplete_Rides_Reason

FROM bookings

WHERE Incomplete_Rides = "Yes";


