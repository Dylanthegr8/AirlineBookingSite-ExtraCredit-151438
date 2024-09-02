**151438 Dylan Matibe**

**Airline Booking System API**
This project provides a simplified API for managing flights and passengers in an airline booking system. It allows for creating, retrieving, updating, and deleting flight and passenger records. The API is built using Django and Django REST Framework (DRF).

Setup Instructions

1. **Clone the Repository**
   ```bash
   git clone https://github.com/your-username/your-repo-name.git
   cd your-repo-name

2.	**Create and Activate a Virtual Environment**
python -m venv venv
source venv/bin/activate  # On Windows use venv\Scripts\activate

3.	**Install Dependencies**
pip install -r requirements.txt

4.	**Apply Migrations**
python manage.py makemigrations
python manage.py migrate

5.	**Run the Development Server**
python manage.py runserver
The API will be accessible at http://127.0.0.1:8000/.

**Models**

Flight

	•	flight_number: CharField (max length: 10), unique identifier for the flight.
	•	departure: DateTimeField, date and time of departure.
	•	arrival: DateTimeField, date and time of arrival.
	•	origin: CharField (max length: 100), origin airport.
	•	destination: CharField (max length: 100), destination airport.
	•	capacity: IntegerField, total number of seats available on the flight.

The Flight model represents a flight and includes details such as the flight number, departure and arrival times, origin and destination airports, and the total seating capacity.

Passenger

	•	first_name: CharField (max length: 50), first name of the passenger.
	•	last_name: CharField (max length: 50), last name of the passenger.
	•	email: EmailField, unique email address of the passenger.
	•	phone_number: CharField (max length: 15), contact number of the passenger.
	•	flight: ForeignKey to Flight, links the passenger to a specific flight.

The Passenger model represents a passenger associated with a flight. Each passenger has a first name, last name, email address, phone number, and is linked to a flight through a foreign key relationship.

**Serializers**

**FlightSerializer**

Serializes the Flight model fields. It includes all fields from the Flight model, allowing for complete representation and manipulation of flight records.

**PassengerSerializer**

```
Serializes the Passenger model fields. It includes all fields from the Passenger model and embeds flight details using the FlightSerializer. This provides a nested representation of the flight associated with each passenger.

**vViewSets**

FlightViewSet**
	•	Handles CRUD operations for Flight records.
	•	Provides endpoints to list, retrieve, create, update, and delete flights.

PassengerViewSet

	•	Handles CRUD operations for Passenger records.
	•	Provides endpoints to list, retrieve, create, update, and delete passengers.
	•	Supports filtering passengers by flight number using search parameters.