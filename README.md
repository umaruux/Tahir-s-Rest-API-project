# **1. Overview**

This project implements a Smart Campus REST API using JAX-RS and Grizzly to manage rooms, sensors, and sensor readings.

# **2. How to Run**

**Simple steps:**

1. Open project in IntelliJ
2. Run Main.java
3. Open Postman
4. Use: http://localhost:8080/api/v1/


# **3. API Endpoints**

**List like:**

GET /rooms
POST /rooms
GET /rooms/{id}
DELETE /rooms/{id}

GET /sensors
POST /sensors
GET /sensors/{id}

GET /sensors/{id}/readings
POST /sensors/{id}/readings

# **4. Sample CURL (MANDATORY)**

## 1. GET all rooms

curl -X GET http://localhost:8080/api/v1/rooms

## 2. Create a room
curl -X POST http://localhost:8080/api/v1/rooms \
-H "Content-Type: application/json" \
-d '{"id":"LIB-301","name":"Library","capacity":100}'
## 3. Create a sensor
curl -X POST http://localhost:8080/api/v1/sensors \
-H "Content-Type: application/json" \
-d '{"id":"TEMP-1","type":"temperature","roomId":"LIB-301"}'
## 4. Get sensors (with filtering)
curl -X GET "http://localhost:8080/api/v1/sensors?type=temperature"
## 5. Add sensor reading
curl -X POST http://localhost:8080/api/v1/sensors/TEMP-1/readings \
-H "Content-Type: application/json" \
-d '{"id":"R1","timestamp":1710000000,"value":25.5}'

## 6. Get readings
curl -X GET http://localhost:8080/api/v1/sensors/TEMP-1/readings

# 5. Answers to Questions

## Question: 
When returning a list of rooms, what are the implications of returning only
IDs versus returning the full room objects? Consider network bandwidth and client side
processing.

## Question: 
Is the DELETE operation idempotent in your implementation? Provide a detailed
justification by describing what happens if a client mistakenly sends the exact same DELETE
request for a room multiple times.

## Question: 
We explicitly use the @Consumes (MediaType.APPLICATION_JSON) annotation on
the POST method. Explain the technical consequences if a client attempts to send data in
a different format, such as text/plain or application/xml. How does JAX-RS handle this
mismatch?

## Question: 
You implemented this filtering using @QueryParam. Contrast this with an alternative
design where the type is part of the URL path (e.g., /api/vl/sensors/type/CO2). Why
is the query parameter approach generally considered superior for filtering and searching
collections?

## Question: 
Discuss the architectural benefits of the Sub-Resource Locator pattern. How
does delegating logic to separate classes help manage complexity in large APIs compared
to defining every nested path (e.g., sensors/{id}/readings/{rid}) in one massive controller
class?

## Question:
Why is HTTP 422 often considered more semantically accurate than a standard
404 when the issue is a missing reference inside a valid JSON payload? 

## Question: 
From a cybersecurity standpoint, explain the risks associated with exposing
internal Java stack traces to external API consumers. What specific information could an
attacker gather from such a trace?
