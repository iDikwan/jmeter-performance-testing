# Performance Testing and Bottleneck Analysis of a REST API Using Apache JMeter

## 📌 Target API
https://jsonplaceholder.typicode.com/posts

## 🛠 Tool Used
Apache JMeter

## 🧪 Test Types
- Load Test  
- Stress Test  
- Soak Test  

---

## 📖 Introduction
Performance testing evaluates how a system behaves under different loads. This study focuses on analyzing the performance of a REST API using Apache JMeter. The objective is to examine system responsiveness, throughput, and reliability under different testing conditions.

---

## ⚙️ Test Setup
- Tool: Apache JMeter  
- Method: GET  
- Protocol: HTTPS  

---

## 🔍 Load Test

The Load Test was conducted to evaluate the performance of the REST API under normal user load conditions. The objective is to measure response time, throughput, and error rate when multiple users access the system simultaneously.

Initially, the following API was selected for testing:

https://reqres.in/api/users?page=2

However, all requests resulted in a 100% error rate. Upon investigation, the issue was caused by a missing API key requirement. The API rejected all requests because authentication was required, making it unsuitable for unauthenticated performance testing using Apache JMeter.

This demonstrates a real-world limitation where APIs enforce access control mechanisms that block automated testing tools unless proper credentials are provided.

To resolve this, the testing target was changed to:

https://jsonplaceholder.typicode.com/posts

This API is designed for testing and allows unrestricted access, making it more suitable for performance evaluation.

The final test configuration was as follows:

- Tool: Apache JMeter  
- HTTP Method: GET  
- Number of Users: 30–50  
- Ramp-Up Period: 30–50 seconds  
- Loop Count: 5–10  
- Timer: 2000–5000 ms delay  

The Load Test results are summarized below:

- Total Requests: 2150  
- Average Response Time: 241 ms  
- Minimum Response Time: 24 ms  
- Maximum Response Time: 4558 ms  
- Throughput: 1.8 requests/sec  
- Error Rate: **46.51%**  

### 📸 Screenshots

#### Thread Group Setup
![Load-Thread-Group](Load-Thread-Group.png)

#### HTTP Request Configuration
![Load-HTTP-Req](Load-HTTP-Req.png)

#### Aggregate Report
![Load-Aggregate](Load-Aggregate.png)

#### Graph Results
![Load-Graph-Result](Load-Graph-Result.png)

### 🧠 Analysis

The Load Test results indicate that the API performs efficiently in terms of response time, with an average response time of 241 ms. However, a relatively high error rate of 46.51% was observed during the test.

This shows that while the API can process requests quickly, it cannot reliably handle repeated concurrent requests. A significant portion of requests failed during execution.

The failures are most likely caused by external limitations such as API rate limiting, request throttling, or restrictions on automated traffic. This means the bottleneck is not due to slow processing, but due to imposed access restrictions by the API provider.

### ⚠️ Bottleneck

The primary bottleneck identified is:

✅ External API Rate Limiting and Request Throttling  

This indicates that the system restricts repeated or high-frequency requests, resulting in a high number of failed responses under load conditions.

### ✅ Conclusion (Load Test)

The Load Test demonstrates that while the API provides fast response times, it lacks stability under continuous concurrent load. The high error rate highlights a critical limitation caused by external system policies rather than internal performance issues.

This confirms that the testing successfully identified a bottleneck, fulfilling the objective of analyzing system behavior under load.

---

## 🔥 Stress Test
(To be completed)

---

## ⏳ Soak Test
(To be completed)

---

## 📊 Results Summary

| Test | Response Time | Throughput | Errors |
|------|--------------|------------|--------|
| Load | 241 ms | 1.8/sec | 46.51% |
| Stress |            |            |        |
| Soak |              |            |        |

---

## 🎥 Demonstration Video
(Add your YouTube link here)
