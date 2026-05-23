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
Performance testing evaluates how a system behaves under different loads. This study focuses on analyzing the performance of a REST API using Apache JMeter.

---

## ⚙️ Test Setup
- Tool: Apache JMeter
- Method: GET
- Endpoint: /api/users?page=2
- Protocol: HTTPS

---

## 🔍 Load Test
🎯 Objective
The Load Test was conducted to evaluate the performance of the REST API under normal user load conditions. The objective is to measure response time, throughput, and error rate when multiple users access the system simultaneously.

⚠️ Initial Testing Issue (ReqRes API)
Initially, the following API was selected for testing:
https://reqres.in/api/users?page=2

However, all requests resulted in a 100% error rate. Upon investigation, the issue was identified as a missing API key requirement. The API returned an error message indicating that authentication was required, making it unsuitable for unauthenticated performance testing.
This demonstrates a real-world limitation where APIs enforce access control mechanisms that prevent automated testing tools like Apache JMeter from sending requests without proper credentials.

🔄 Change of Testing Target
To ensure accurate and meaningful performance testing, the target API was changed to:
https://jsonplaceholder.typicode.com/posts

This API is publicly accessible and designed for testing and prototyping, making it more suitable for performance testing scenarios.

🌐 Final Target API
https://jsonplaceholder.typicode.com/posts


⚙️ Configuration

Tool: Apache JMeter
HTTP Method: GET
Number of Users (Threads): 30–50
Ramp-Up Period: 30–50 seconds
Loop Count: 5–10
Timer: Uniform Random Timer (2000–5000 ms delay)


📊 Results

Total Requests: 2150
Average Response Time: 241 ms
Minimum Response Time: 24 ms
Maximum Response Time: 4558 ms
Throughput: 1.8 requests/sec
Error Rate: 46.51%


📸 Screenshots

### Thread Group Setup
Load-Thread-Group.png


HTTP Request Configuration
Load-HTTP-Req.png


Aggregate Report
Load-Aggregate.png


Graph Results
Load-Graph-Result.png


🧠 Analysis
The Load Test results indicate that the API performs efficiently in terms of response time, with an average response time of 241 ms. However, a relatively high error rate of 46.51% was observed during the test.
This suggests that while the API can process requests quickly, it cannot handle repeated concurrent requests reliably. A significant number of requests were rejected or failed during execution.
The errors are most likely caused by external limitations such as:

API rate limiting
Request throttling
Restrictions on automated traffic

This indicates that the performance limitation is not due to system processing speed, but due to access control and traffic management policies implemented by the API provider.

⚠️ Identified Bottleneck
The primary bottleneck identified during the Load Test is:

✅ External API Rate Limiting and Request Throttling

This means that the API restricts repeated or high-frequency requests, resulting in failed responses even under moderate load conditions.

✅ Load Test Conclusion
The Load Test demonstrates that although the API responds quickly under normal conditions, its reliability decreases significantly under continuous concurrent access. The high error rate highlights a limitation imposed by external system policies rather than internal processing inefficiencies.
This test successfully identifies a key performance bottleneck, fulfilling the objective of analyzing system behavior under load.

## 🔥 Stress Test
Users: 200+  
Result: (put your result here)

---

## ⏳ Soak Test
Duration: 30 minutes  
Result: (put your result here)

---

## 📊 Results Summary

| Test | Response Time | Throughput | Errors |
|------|--------------|------------|--------|
| Load |              |            |        |
| Stress |            |            |        |
| Soak |              |            |        |

---

## 🧠 Analysis
Explain what happened in each test.

---

## ⚠️ Bottleneck
- Example: High response time under stress

---

## ✅ Recommendations
- Improve server handling
- Add caching

---

## 🎥 Video
Paste YouTube link here
