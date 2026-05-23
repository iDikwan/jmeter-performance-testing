# Performance Testing and Bottleneck Analysis of a REST API Using Apache JMeter

---

## 📌 Target API
https://jsonplaceholder.typicode.com/posts

---

## 🛠 Tool Used
Apache JMeter

---

## 🔄 How It Works

JMeter (client) sends HTTP GET requests to the API server.

JMeter ─────────► jsonplaceholder.typicode.com  
(send request)

JMeter ◄───────── jsonplaceholder.typicode.com  
(receive response)

JMeter records:
- Response time  
- Throughput  
- Error rate  

The results may vary depending on network latency, server load, and request patterns.

---

## 🧪 Test Types

### ✅ Load Test
Simulates normal user traffic to evaluate system performance under expected conditions.

### ✅ Stress Test
Pushes the system beyond its capacity to identify breaking points and performance degradation.

### ✅ Soak Test
Tests system stability over a long period of sustained usage.

---

## 📖 Introduction
Performance testing evaluates how a system behaves under different loads. This study focuses on analyzing the performance of a REST API using Apache JMeter. The objective is to examine system responsiveness, throughput, and reliability under different testing conditions.

---

## ❗ Problem Statement

Modern APIs must handle varying user loads efficiently. This project aims to evaluate how a REST API performs under different traffic conditions, including normal usage and high load, to identify potential bottlenecks and performance limitations.

---

## ⚙️ Test Setup

- Tool: Apache JMeter  
- Protocol: HTTPS  
- Method: GET  
- Loop Count: 10  
- Ramp-Up Period: 10 seconds  
- Timer: None  

---

## 🔍 Load Test

The Load Test was conducted to evaluate system performance under normal user conditions using a controlled setup.

### ✅ Configuration
- Number of Users: 10  
- Ramp-Up: 10 seconds  
- Loop Count: 10  
- Timer: None  

---

### 📊 Results
- Total Requests: 10650  
- Average Response Time: 200 ms  
- Throughput: 1.4 requests/sec  
- Error Rate: **9.40%**  

---

### 📸 Screenshots

#### Thread Group Setup
![Load-Thread-Group](Load-Thread-Group.png)

#### HTTP Request Configuration
![Load-HTTP-Req](Load-HTTP-Req.png)

#### Aggregate Report
![Load-Aggregate](Load-Aggregate.png)

#### Graph Results
![Load-Graph-Result](Load-Graph-Result.png)

---

### 🧠 Analysis

The Load Test results indicate that the API performs efficiently under normal usage conditions, with an average response time of 200 ms.

An error rate of 9.40% was observed, which indicates that most requests were successfully processed, but a small percentage failed. Additionally, occasional high response times were recorded, suggesting temporary delays during certain requests.

Overall, the system demonstrates good performance with minor reliability limitations.

---

### ⚠️ Identified Bottleneck

✅ Moderate error rate indicates **minor reliability limitations under continuous usage**

---

### ✅ Conclusion (Load Test)

The Load Test demonstrates that the API can handle normal traffic efficiently with fast response time and relatively low error rate. However, minor instability exists during repeated requests.

---

## 🔥 Stress Test

The Stress Test evaluates system behavior under heavy load by significantly increasing the number of users while maintaining the same configuration.

---

### ✅ Configuration
- Number of Users: 200  
- Ramp-Up: 10 seconds  
- Loop Count: 10  
- Timer: None  

---

### 📊 Results
- Total Requests: 12650  
- Average Response Time: 183 ms  
- Throughput: 1.6 requests/sec  
- Error Rate: **7.91%**  

---

### 📸 Screenshots

#### Thread Group Setup
![Stress-Thread-Group](Stress-Thread-Group.png)

#### Aggregate Report
![Stress-Aggregate](Stress-Aggregate.png)

#### Graph Results
![Stress-Graph](Stress-Graph.png)

---

### 🧠 Analysis

The Stress Test produced an interesting result where the error rate (7.91%) was lower than the Load Test (9.40%), despite a much higher number of users.

This shows that system performance depends not only on user count but also on how requests are distributed.

With a ramp-up period of 10 seconds, requests are introduced gradually rather than all at once. This avoids sudden spikes and allows the system to process requests more efficiently, resulting in improved throughput and lower error rate.

---

### ⚠️ Identified Bottleneck

✅ System is sensitive to **traffic patterns rather than just user volume**

Performance degradation is more likely under burst traffic conditions.

---

### ✅ Conclusion (Stress Test)

The system performs efficiently even under higher user load when requests are evenly distributed. This indicates that traffic pattern plays a significant role in system stability.

---

## 📊 Results Summary

| Test | Users | Response Time | Throughput | Error Rate |
|------|------|--------------|------------|-----------|
| Load | 10 | 200 ms | 1.4/sec | 9.40% |
| Stress | 200 | 183 ms | 1.6/sec | 7.91% |
| Soak | - | - | - | - |

---

## 🧠 Overall Analysis

The results demonstrate that increasing the number of users does not always negatively impact performance. Instead, system behavior depends heavily on request distribution patterns.

Gradual request distribution allows the server to handle higher load more efficiently, while sudden bursts may cause failures.

This highlights the importance of considering both user load and traffic behavior in performance testing.

---

## ⏳ Soak Test
(To be completed)

---

## 🎥 Demonstration Video
(Add your YouTube link here)
