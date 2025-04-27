# SQL-Project
SQL/No SQL Class project

```python
pip install pymongo
```

    Requirement already satisfied: pymongo in /opt/anaconda3/lib/python3.11/site-packages (3.11.0)
    Note: you may need to restart the kernel to use updated packages.



```python
import pymongo
```


```python
from pymongo import MongoClient
import urllib.parse


username = urllib.parse.quote_plus('pythonclass')

password = urllib.parse.quote_plus('pythonclass')
```


```python
client = MongoClient('mongodb+srv://%s:%s@cluster0.wrwzs.mongodb.net/?retryWrites=true&w=majority&appName=Cluster0' % (username, password))

```


```python
#create database
db = client.airline
```


```python
#create collection within database
collection = db.reservations
```


```python
#This is the same DBMS that you used for project one. The non-relational model can be a 
#single sample document containing all the tables that you designed in Project 1.

```


```python
#create #single sample document
 #added another pseudo passenger to show one to many booking agents to passenger

    # booking_agents    
Bookings = {
  
    "agent_id":34 ,   
    "agent_name": "Woods James"  , 
    "agent_details": "Senior",    
   
# Itinerary_reservations
    "reservation_id": 9876,
    "Agent_id": 34,
    "passenger_id": 3829,  
    "reservation_status_code": 2849,
    "Ticket_type_code": 111,
    "Travel_class_code": 284,
    "Date_reservation_made": "2008-03-03",
    "Number_in_party": 1,
  
 # Passengers
    "passengers": [
        
        {
        "passenger_id": 3829,     
        "first_name": "Mary",
        "Middle_name": "Joy",
        "last_name": "Lewis",
        "email": "mjl@gmail.com",
        "phone_number": 2014446584},
        
   

        {"passenger_id": 3937,     
        "first_name": "Jenny",
        "Middle_name": "Joseph",
        "last_name": "Dobbs",
        "email": "JJD@gmail.com",
        "phone_number": 2015519984}
    ],
    
  # Legs 
    "legs": [
    {
    "Leg_id": 1,
    "flight_number": 888,
    "Origin_airport": 'GUTR',
    "Destination_airport": 'WAGY',
    "aircraft_type_code": "BBB",
    "valid_from_date": "2015-05-15",
    "valid_to_date": "2016-05-15",
    "flight_cost": 800.00}
    ],
    
 # Reservation_payments
    "reservation_payments": [
    {
    "reservation_id": 9876,
    "Payment_id": 44,
    "Payment_status_code": 29,
    "Payment_date": "2008-02-03",
    "Payment_amount": 450.00
    }
    ],

# Flights.Itinerary_legs
    "flights_itinerary_legs": [
    {
    "reservation_id":9876,
    "Leg_id": 1}
    ],
 
 # Flights.legs
    "flights_legs": [
    {
    "Leg_id": 1,
    "Flight_number": 999, 
    "Origin_airport": "HART", 
    "Destination_airport": "SEGIG",
    "Actual_departure_time": "14:30:00",
    "Actual_arrival_time": "17:00:00"}
    ],
    
 # Flights.airports
    "flights_airports": [
    {
    "Origin_airport_code": "HRT", 
    "airport_name": "HART", 
    "airport_location": "Wyoming", 
    "other_details": "OPEN"}
    ],
        
  # Flight_schedules
    "flight_schedules": [
    {
    "Flight_number": 999, 
    "Airline_code": 123, 
    "Usual_airport_type_code": "AA", 
    "Origin_airport_code": "HRT",
    "Destination_airport_code": "SEG", 
    "Departure_date_time": "2018-03-14 01:59:00", 
    "Arrival_date_time": "2018-03-14 03:59:00"}
    
    ]
}
```


```python
# Insert the blog post document into the collection
result= collection.insert_one(Bookings)


```


```python
inserted_document = collection.find_one({"agent_id": result.inserted_id})

```


```python

```
