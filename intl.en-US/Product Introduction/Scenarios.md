# Scenarios

ECS is a highly flexible solution that can be used independently as a simple web or application server, or used together with other Alibaba Cloud services to deliver advanced solutions.

**Note:** This topic describes some typical scenarios of ECS and how to take advantage of the benefits of cloud computing while using ECS.

## Official websites and lightweight web applications

A new website has low traffic and requires only a low-configuration ECS instance to run web applications such as Apache and NGINX, host databases, and store files. As your website develops, you can upgrade the ECS instance configurations or add ECS instances at any time to provision sufficient resources for handling traffic spikes.

## Multimedia and high-concurrency applications or websites

ECS can be used with Object Storage Service \(OSS\) to store static images, videos, or downloaded packages to reduce storage costs. In addition, ECS can work with Alibaba Cloud Content Delivery Network \(CDN\) and Server Load Balancer \(SLB\) to shorten waiting time, reduce public bandwidth costs, and improve service availability. For more information, see [What is OSS?](/intl.en-US/Product Introduction/What is OSS?.md), [What is Alibaba Cloud CDN?](/intl.en-US/Product Introduction/What is Alibaba Cloud CDN?.md), and [What is SLB?](/intl.en-US/Product Introduction/What is SLB?.md)

## Databases with high I/O requirements

ECS supports databases with high I/O requirements, such as OLTP and NoSQL databases. A high-configuration I/O optimized ECS instance can be used with ESSDs to achieve high I/O concurrency and higher data reliability. Alternatively, multiple lower-configuration I/O optimized ECS instances can be used with SLB to deliver a high availability architecture. For more information, see [Enhanced SSDs](/intl.en-US/Block Storage/Block Storage overview/Enhanced SSDs.md) and [What is SLB?](/intl.en-US/Product Introduction/What is SLB?.md)

## Applications and websites with sharp traffic fluctuations

Some applications may experience sharp traffic fluctuations within a short period of time. When ECS is used with Auto Scaling, the number of ECS instances is automatically adjusted based on traffic. This way, you can meet the changing resource requirements at a low cost. ECS can also work with SLB to deliver a high availability architecture. For more information, see [What is Auto Scaling?](/intl.en-US/Product Introduction/What is Auto Scaling?.md) and [What is SLB?](/intl.en-US/Product Introduction/What is SLB?.md)

## Big data and real-time online and offline analysis

ECS provides big data instance families that support Hadoop distributed computing, log processing, and large data warehouses. Big data instance families adopt a local storage architecture, which helps deliver better network performance for Hadoop and Spark clusters while providing abundant storage space and higher storage performance. For more information, see [Big data instance families](/intl.en-US/Instance/Instance type families/Big data instance families.md).

## AI applications such as machine learning and deep learning

ECS allows you to use GPU-accelerated compute optimized instances to build AI applications based on frameworks such as TensorFlow. Such instances have lower computing capacity requirements for clients and are suitable for scenarios such as image processing and real-time online rendering for cloud gaming and AR/VR applications. For more information, see [GPU-accelerated compute optimized instance families](/intl.en-US/Instance/Instance type families/Compute optimized type family with GPU/Compute optimized instance families with GPU capabilities.md).

## More cases

For more scenarios of ECS, see [Alibaba Cloud solutions](https://www.alibabacloud.com/solutions).

