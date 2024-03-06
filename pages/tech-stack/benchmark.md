# Benchmark

One of the goals of FeatBit is to create a scalable and fast real-time feature flag management service. For this point, we focus on the capacity to handle concurrent users, this mainly depends on the performance of the Evaluation Server service. The document gives a performance report of the Evaluation Server in an isolated minimum environment.

## Test objectives

We need to find out if Evaluation Server meets the performance requirements as specified below.

Evaluation Server needs to be able to handle 1000 new connections per second providing the industry standard level of service in terms of response time and error rate. The 99th pencentile (P99) response time needs to be less than 200 milliseconds and the acceptable error rate is less than 1%. With this criteria, we would assure the max capacity of Evaluation Server while offering a high reliable service.

The max number of user connections FeatBit can hold for a given time is not covered in this document as we observed that the CPU and memory usages are low when there is no data synchronization happening. The ability to push changes to connected users would be covered in future report.

## General test conditions

The following test conditions are most appropriate to simulate the real life usage.

* Number of new connections established (including data synchronization) per second
* The average P99 response time **(1)**
* User actions: make a data synchronization request after the connection is established

**(1)** response time: the time passed before data sync request sent and after the response is received.

## Environment

We selected the commonly available AWS EC2 service to host the Evaluation Server service. The instance type is **t2.micro with 1 vCPU and 1 GiB RAM**, which is free tier eligible.

We used EC2 instance to execute our tests, this could minimize the network impact to the results.

## Tests performed

**Test duration**: 180 seconds

**Load type**: ramp-up from 0 to 1000, 1100, 1200 new connections per second

**Number of test**: 10 for each of the 1000, 1100 and 1200 per second use case

## Test results

The performed test has shown that the Evaluation Server preserves the desired quality of service only with a limit load. with until 1100 new connections per second, when it reaches 1200/s, some errors are observed.

**The response time**

<table><thead><tr><th width="378">Number of new connections per second</th><th width="100">Avg (ms)</th><th width="100">P95 (ms)</th><th>P99 (ms)</th></tr></thead><tbody><tr><td>1000</td><td>5.42</td><td>24.7</td><td>96.70</td></tr><tr><td>1100</td><td>9.98</td><td>55.51</td><td>170.30</td></tr><tr><td>1200</td><td>34.17</td><td>147.91</td><td>254.60</td></tr></tbody></table>

**Peak CPU Utilization %**

| Number of new connections per second | Ramp-up stage | Stable stage |
| ------------------------------------ | ------------- | ------------ |
| 1000                                 | 82            | 26           |
| 1100                                 | 88            | 29           |
| 1200                                 | 91            | 31           |

**Peak Memory Utilization %**

| Number of new connections per second | Ramp-up stage | Stable stage |
| ------------------------------------ | ------------- | ------------ |
| 1000                                 | 55            | 38           |
| 1100                                 | 58            | 42           |
| 1200                                 | 61            | 45           |

## Conclusion

With a minimum hardware setting: **AWS EC2 t2.micro (1 vCPU + 1 G RAM)**, the Evaluation Server is capable of providing a reliable service for until 1100 new connections per second, the maximum number of connections held for a given time reaches 22000 (this is not the limit).

The web server resource utilization measured during the testing shows that the bottleneck of the hardware is the CPU, which is comprehensible as CPU is intensely used to evaluate the feature flags during the data synchronization stage. By using an instance with more vCPUs (or compute optimized instances), we can surely increase the capacity of number of max new connections per second.

We believe the reported performance is largely enough for small businesses with a negligible cost (free tier eligible). The capacity can be multiplied easily by scaling the service horizontally when the business grows. &#x20;

## Data set used for the tests

In the above tests, we used 5 feature flags and 2 segments. Test data is attached below.

[Feature flags test sample file](https://github.com/featbit/featbit-docs/blob/main/pages/tech-stack/assets/flags.json)

[Segments test sample file](https://github.com/featbit/featbit-docs/blob/main/pages/tech-stack/assets/segments.json)

