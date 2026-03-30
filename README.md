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

# **4. Sample cURL (MANDATORY)**

They REQUIRE this.

Add at least 5:

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

5. Answers to Questions
