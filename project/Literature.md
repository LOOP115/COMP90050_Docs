# Literature



##### 1 Self-Driving Database Management Systems 6 2017

The paper discusses the concept of a "self-driving" database management system (DBMS) that is designed for autonomous operation. The authors argue that existing DBMSs still require human intervention and are reactionary in nature, fixing problems after they occur. They propose a new architecture called Peloton, which is the first self-driving DBMS. Peloton uses algorithmic advancements in deep learning and adaptive database architectures to optimize the system for the current workload and predict future workload trends. The DBMS can support previous tuning techniques without human intervention and enable new optimizations that are not possible with human experts. The paper also discusses the challenges of workload understanding, resource utilization forecasting, and efficient application of optimizations. Peloton's architecture includes components for workload classification, workload forecasting, action generation, and control framework. The authors conclude that self-driving DBMSs are now achievable and present initial results on using Peloton's deep learning framework for workload forecasting and action deployment.



##### 2 Query-based Workload Forecasting for Self-Driving Database Management Systems 15 2018

The paper discusses the need for query-based workload forecasting in self-driving database management systems (DBMS). The authors propose a forecasting framework called QueryBot 5000 that predicts the expected arrival rate of queries in the future based on historical data. The framework uses the logical composition of queries in the workload rather than the amount of physical resources used for query execution. It provides multiple horizons with different aggregation intervals and includes a clustering-based technique to reduce the number of forecasting models to maintain. The authors evaluate their approach by comparing it against other state-of-the-art models on three real-world database traces. They demonstrate the effectiveness of their models in selecting indexes and show that the framework can efficiently forecast the expected future workload with minimal loss in accuracy.



##### 3 Self-Driving: From General Purpose to Specialized DBMSs 4 2018

The paper discusses the concept of self-driving database systems, which utilize workload-driven optimization and machine learning techniques to optimize database performance without human intervention. The authors propose a generalized framework that enables the integration of self-driving capabilities into database systems, allowing them to be tailored to specific use cases. They also present their approach to solving the index selection problem using real-world data on the Hyrise database system. The paper highlights the need for self-driving database systems due to the increasing complexity of workloads, the shift to cloud deployments, and the growing number of configuration options. The authors identify three main research areas for self-driving databases: tuning, feedback loop, and forecasting. They discuss the limitations of existing solutions and present their approach and future research plans.



##### 4 External vs. Internal: An Essay on Machine Learning Agents for Autonomous Database Management Systems 15 2019

This paper discusses the use of machine learning agents for automated tuning of database management systems (DBMSs). The authors explore two approaches for integrating machine learning agents in a DBMS: building an external tuning controller that treats the DBMS as a black-box, or integrating the machine learning agents natively in the DBMS's architecture. The paper discusses the trade-offs of these approaches and presents two projects from Carnegie Mellon University as examples. The authors also provide background information on previous methods for automated DBMS tuning, such as heuristic-based and cost-based optimization algorithms. They highlight the limitations of these methods and explain how machine learning can potentially provide faster approximations for optimization problems. The paper concludes by discussing the implications of integrating machine learning in DBMSs for tuning and the challenges associated with it.



##### 5 Replicated Training in Self-Driving Database Management Systems 61 2019

The thesis discusses the challenges of training machine learning models in self-driving DBMSs and proposes a technique called Replicated Training to address the performance overhead of data generation. The effectiveness of the technique is evaluated in a distributed environment using NoisePage, a self-driving DBMS. The results show that Replicated Training eliminates the performance overhead in the master node while ensuring that replicas keep up with the master with low delay. The thesis also demonstrates that Replicated Training produces ML models with accuracies comparable to those trained solely on the master node.



##### 6 Self-driving database systems: a conceptual approach 23 2020

The paper discusses the concept of self-driving database systems, which are capable of autonomously adjusting their configuration and tuning tasks. The authors present a component-based framework for self-driving database systems that enables easy integration and development of self-management functionality. They propose a linear programming algorithm to optimize multiple dependent features and demonstrate the applicability and scalability of their approach with reproducible examples. The paper also highlights the challenges and considerations in designing self-driving database systems, such as workload prediction and robustness. The authors review related work in the field and discuss the integration and design decisions in their framework. They also discuss the importance of accurate cost estimation and workload modeling in self-driving database systems. Finally, the paper presents future research directions and conclusions.



##### 7 DBMind: a self-driving platform in openGauss 4 2021

The paper introduces DBMind, a self-driving platform for database management. The platform provides three autonomous capabilities: self-monitoring, self-diagnosis, and self-optimization.

In the self-monitoring capability, DBMind collects database metrics and detects anomalies using statistical methods and prediction algorithms. It can identify slow queries, IO contention, and other potential risks.

The self-diagnosis capability utilizes an LSTM model to analyze the root causes of anomalies and automatically detect the root causes from a pre-defined failure hierarchy. It optimizes the diagnosis model by analyzing historical data and requires minimal expert labeling of anomaly cases.

The self-optimization capability automatically optimizes the database performance using learning-based techniques. This includes deep reinforcement learning based knob tuning, reinforcement learning based index selection, and encoder-decoder based view selection.

DBMind is implemented in the open source database openGauss and has been demonstrated in real scenarios. It offers effective self-monitoring, diagnosis, and optimization features, saving time for database administrators and improving overall performance.



##### 8 Self-Driving Database Management Systems: Forecasting, Modeling, and Planning 125 2021

The thesis discusses the challenges of deploying and administering database management systems and proposes a novel architecture for a self-driving DBMS that enables automatic system management. The architecture consists of three frameworks: workload forecasting, behavior modeling, and action planning. The workload forecasting framework predicts query arrival rates, the behavior modeling framework predicts the runtime behavior of the DBMS, and the action planning framework generates optimization actions based on these predictions. The architecture aims to remove the need for human administration and provide explanations for its decisions.



##### 9 MB2: Decomposed Behavior Modeling for Self-Driving Database Management Systems 14 2021

The paper introduces a framework called ModelBot2 (MB2) for constructing and maintaining prediction models using machine learning in self-driving database management systems (DBMSs). The goal of a self-driving DBMS is to manage itself automatically, but a critical problem is predicting the DBMS's runtime behavior and resource consumption. MB2 decomposes the DBMS's architecture into fine-grained operating units (OUs) and uses machine learning to train models for each OU. These models estimate the runtime and resource consumption of the OUs and their interference during concurrent execution. MB2 also provides a method for generating training data and integrates it into an in-memory DBMS. The results show that MB2's models are more accurate than state-of-the-art models in predicting performance for OLTP and OLAP workloads.



##### 10 Make your database system dream of electric sheep: towards self-driving operation 11 2021

The paper discusses the concept of self-driving database management systems (DBMSs) and presents an implementation approach towards achieving this goal. The authors highlight the difficulties in deploying and administering DBMSs and propose using artificial intelligence and machine learning techniques to automate these tasks.

The proposed system, called NoisePage, has three main components: workload forecasting, behavior modeling, and action planning. The workload forecasting component predicts the future queries of the application based on past arrival rates. The behavior modeling component uses these predictions to estimate the cost and benefit of deploying actions without the need for extensive testing. The action planning component selects actions that improve the system's objective function (e.g., latency, throughput) and automatically applies them.

The authors also discuss the levels of autonomy that a self-driving DBMS can provide, ranging from manual control to full autonomy. They propose a taxonomy of five levels, with Level 5 representing a fully autonomous DBMS that can make decisions and optimize itself without human intervention.

The paper concludes by presenting the architecture of NoisePage and emphasizing the importance of software engineering design principles in developing self-driving DBMSs. The authors believe that these principles, combined with machine learning methods, can enable a DBMS to support autonomous operations and reduce the cost and complexity of managing complex applications.



##### 11 DBA bandits: Self-driving index tuning under ad-hoc, analytical workloads with safety guarantees 12 2021

The paper titled "DBA bandits: Self-driving index tuning under ad-hoc, analytical workloads with safety guarantees" proposes a self-driving approach to online index selection in databases. The current manual methods of index tuning are not suitable for dynamic environments with ad-hoc workloads. The paper suggests using multi-armed bandits, a form of sequential decision making under uncertainty, to automate the index selection process. The proposed approach learns the benefits of different index structures through exploration and direct performance observation, without relying on cost models. The paper presents empirical results that demonstrate the superiority of the proposed approach over a state-of-the-art commercial tuning tool, achieving up to 75% speed-up on shifting and ad-hoc workloads.



##### 12 HMAB: Self-Driving Hierarchy of Bandits for Integrated Physical Database Design Tuning 14 2022

The paper titled "HMAB: Self-Driving Hierarchy of Bandits for Integrated Physical Database Design Tuning" proposes a new approach for physical database design tuning. The authors introduce a self-driving approach based on hierarchical multi-armed bandit learners (HMAB) that can work in an integrated space of multiple physical design structures (PDS) while avoiding the full cost of combinatorial search. The proposed approach leverages actual performance observations and strategic exploration to make recommendations for PDS tuning. The paper presents the first learned system to tune both indices and materialized views in an integrated manner. Experimental results show that HMAB outperforms state-of-the-art commercial physical database design tools, achieving up to 96% performance gain. The paper provides a formal definition of the online physical database design tuning problem and discusses the bandit background, including contextual and combinatorial bandits. The proposed HMAB approach consists of two layers, with the first layer responsible for candidate PDS selection and the second layer considering all candidate structures to select the final configuration. The paper also introduces a search method that combines the optimiser knowledge and actual execution statistics to make better recommendations and reduce PDS creation time. Overall, the paper presents a novel approach for physical database design tuning that improves performance compared to existing tools.



##### 13 An Adaptive Column Compression Family for Self-Driving Databases 11 2022

The paper discusses the importance of data compression in modern in-memory databases and proposes a novel adaptive compressor that offers a trade-off between memory requirements and query speed. The compressor achieves better compression than LZ4 while maintaining query speeds close to the fastest existing segment encoders. The authors evaluate the compressor using synthetic data and industry-standard benchmarks integrated into a relational column store. The paper also introduces a segment encoding scheme for autonomous databases where the compressor selection is driven by query patterns to maximize performance. The authors present the design of four segment variants using a compression algorithm called Generalized Deduplication. They compare their proposed segment encoders with commonly used integer compression schemes in columnar databases, including Dictionary Encoding, Frame-of-Reference (FoR), and LZ4. The evaluation is conducted using the Hyrise relational in-memory column store. The paper concludes with the results of the evaluation and proposes future work.



##### 14 Tastes Great! Less Filling! High Performance and Accurate Training Data Collection for Self-Driving Database Management Systems 14 2022

The paper discusses the challenges of collecting training data for self-driving database management systems (DBMS) and presents a framework called TScout (TS) for efficient and accurate data collection. The framework uses internal annotations in the DBMS source code to monitor the system's behavior and generates a kernel-level program to collect metrics from multiple sources. The authors integrated TS with a PostgreSQL-compatible DBMS and measured its ability to collect training data for both OLTP and OLAP workloads. The results show that TS generates training data with only a 7% performance reduction compared to previous methods and improves the accuracy of behavior models by 98% in some cases.



##### 15 Explainable AI for DBA: Bridging the DBA's experience and machine learning in tuning database systems 24 2023

The article discusses the use of artificial intelligence (AI) techniques in the database community to improve the query processing and self-tuning of database systems. The authors propose a framework called Explain-Tun that aims to provide transparency and intelligible explanations for the selection of physical structures in database systems. The framework incorporates AI-based DBMS to explain how to select physical structures and provides decision rules extracted by machine learning (ML) models. The authors also introduce a goal-oriented model to involve the database administrator (DBA) in the optimization process and allow them to manipulate ML models. The framework is evaluated on three use cases, showing the benefits of bridging the DBA's experience with ML in tuning database systems. The article contributes to the field by providing a comprehensible model for selecting physical structures in databases and improving the user experience in understanding and manipulating ML models.



##### 16 Automatic single table storage structure selection for hybrid workload 27 2023

The paper discusses the importance of selecting the appropriate storage structure for database systems in order to optimize performance. It focuses on the challenges faced in hybrid workloads, where the query set and storage structure need to dynamically change. The paper proposes an automatic storage structure selection system based on learning cost, which uses machine learning to build a cost model for the storage engine and a column-oriented data layout generation algorithm. Experimental results show that the proposed system improves the performance of the default storage structure and is compatible with different storage engines. The paper also highlights the need for intelligent and flexible storage structure selection techniques for machine learning workloads. The proposed system aims to replace HTAP databases by leveraging existing databases and selecting the appropriate storage structure based on workload characteristics. The paper provides an overview of the system architecture and methodology.

