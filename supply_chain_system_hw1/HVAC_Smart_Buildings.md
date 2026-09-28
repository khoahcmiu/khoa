# Taxonomy and Literature Review of HVAC Control and Infrastructure in Smart Buildings

## Executive Summary
Heating, Ventilation, and Air Conditioning (HVAC) systems represent the primary energy consumption category in the global building sector, often accounting for over 40% of total usage. This report presents a systematic taxonomy and literature review of recent developments in HVAC control strategies and the technological infrastructures that support them in the context of smart buildings. The analysis categorizes control methods into traditional rule-based, Model Predictive Control (MPC), learning-based, and intelligent hybrid systems. 

A significant finding of this review is the increasing reliance on data-driven approaches, particularly Deep Reinforcement Learning (DRL) and ensemble machine learning algorithms, which have demonstrated energy savings between 20% and 30% while maintaining or enhancing occupant thermal comfort. The report also details the sophisticated technological stack required for these systems, involving Internet of Things (IoT) sensor networks, edge-cloud computing platforms, and advanced human activity recognition technologies such as computer vision and wearables. Despite these advancements, challenges related to high upfront costs, data quality, and system interoperability remain significant barriers to widespread deployment. The review concludes by highlighting the need for scalable, ethical, and grid-responsive building automation solutions.

## Table of Contents
1. [Introduction](#1-introduction)
2. [Taxonomy of HVAC Control Strategies](#2-taxonomy-of-hvac-control-strategies)
    * 2.1 Traditional and Rule-Based Control
    * 2.2 Model Predictive Control (MPC) and Optimization
    * 2.3 Learning-Based and Data-Driven Approaches
    * 2.4 Intelligent and Hybrid Control Frameworks
3. [Technological Infrastructure and Architectures](#3-technological-infrastructure-and-architectures)
    * 3.1 Advanced Sensing and IoT Integration
    * 3.2 Human Activity Recognition and Occupancy Detection
    * 3.3 Computational Platforms and Software Frameworks
4. [Findings and Comparative Analysis](#4-findings-and-comparative-analysis)
5. [Limitations of the Evidence](#5-limitations-of-the-evidence)
6. [Research Gaps and Future Directions](#6-research-gaps-and-future-directions)
7. [Conclusion](#7-conclusion)

---

## 1. Introduction
The global drive toward sustainability has placed the building sector under intense scrutiny, as it is a major contributor to greenhouse gas emissions and energy consumption [[#^ref-6|[6]]], [[#^ref-31|[31]]]. Within this sector, HVAC systems are the most critical components for both energy management and occupant well-being [[#^ref-1|[1]]], [[#^ref-37|[37]]]. The concept of the "Smart Building" has emerged as a solution, integrating advanced Information and Communication Technologies (ICT) to create environments that are self-optimizing, responsive, and human-centered [[#^ref-34|[34]]], [[#^ref-51|[51]]].

Modern building automation aims to solve a complex multi-objective problem: minimizing energy costs and carbon footprint while maximizing Indoor Environmental Quality (IEQ), which includes thermal comfort, air quality, and lighting [[#^ref-3|[3]]], [[#^ref-12|[12]]]. Traditional HVAC management, relying on static schedules and reactive logic, is increasingly inadequate for handling the dynamic nature of modern office and residential spaces [[#^ref-23|[23]]], [[#^ref-27|[27]]]. Consequently, researchers are exploring proactive control strategies that leverage predictive analytics, Big Data, and Artificial Intelligence (AI) to optimize building performance in real-time [[#^ref-18|[18]]], [[#^ref-55|[55]]].

## 2. Taxonomy of HVAC Control Strategies
The literature reveals a clear evolution in HVAC control, which can be categorized into four primary taxonomic groups based on their operational logic and degree of intelligence.

### 2.1 Traditional and Rule-Based Control
Traditional control strategies remain the foundation of most existing building management systems (BMS).
- **On/Off and Hysteresis Control**: These systems operate on simple binary logic, activating heating or cooling when a threshold is crossed [[#^ref-9|[9]]], [[#^ref-25|[25]]]. While simple to implement, they often result in significant temperature fluctuations and mechanical wear [[#^ref-25|[25]]].
- **Proportional-Integral-Derivative (PID) Control**: PID loops provide continuous control by adjusting system outputs (e.g., fan speed, valve position) to minimize the error between a setpoint and the measured variable [[#^ref-13|[13]]], [[#^ref-21|[21]]]. Despite their widespread use, PID controllers are reactive and struggle to adapt to the non-linear and time-varying nature of thermal loads in complex buildings [[#^ref-5|[5]]], [[#^ref-17|[17]]].
- **Scheduling and Manual Control**: Many buildings still operate on fixed schedules (e.g., HVAC active only during business hours) or rely on manual adjustments by occupants, which are prone to human error and substantial energy waste [[#^ref-11|[11]]], [[#^ref-23|[23]]].

### 2.2 Model Predictive Control (MPC) and Optimization
MPC is a sophisticated, model-based approach that has gained significant traction in smart building research [[#^ref-1|[1]]], [[#^ref-41|[41]]].
- **Mechanism**: MPC uses a dynamic model of the building's thermal behavior to predict future states over a defined horizon. It solves an optimization problem at each time step to determine the control actions that minimize a cost function (typically energy use or cost) while respecting constraints like occupant comfort [[#^ref-13|[13]]], [[#^ref-28|[28]]].
- **Evolution**: The field is moving from "white-box" models, which require detailed physical parameters of the building, toward "gray-box" and "black-box" models that use data-driven identification techniques [[#^ref-1|[1]]]. Hybrid solvers and metaheuristic algorithms are increasingly used to handle the massive optimization problems associated with large-scale MPC implementations [[#^ref-1|[1]]], [[#^ref-13|[13]]].
- **Applications**: MPC is particularly effective for peak load shifting and integrating renewable energy sources, as it can pre-condition spaces during periods of low electricity prices or high solar generation [[#^ref-32|[32]]], [[#^ref-44|[44]]].

### 2.3 Learning-Based and Data-Driven Approaches
The proliferation of building data has enabled the development of "model-free" control strategies that learn directly from historical and real-time data [[#^ref-47|[47]]], [[#^ref-48|[48]]].
- **Reinforcement Learning (RL)**: RL agents, such as Deep Reinforcement Learning (DRL) and Multi-Agent Reinforcement Learning (MARL), learn optimal control policies through trial and error, guided by a reward signal that balances energy efficiency and comfort [[#^ref-2|[2]]], [[#^ref-52|[52]]]. Advanced frameworks like MADDPG (Multi-Agent Deep Deterministic Policy Gradient) allow for coordinated control across multiple zones with continuous action spaces [[#^ref-11|[11]]].
- **Ensemble Machine Learning**: Recent studies have demonstrated the power of ensemble methods, such as Random Forest (RF), XGBoost, and Histogram Gradient Boosting (HGB), for predicting occupant thermal sensation votes (TSV) [[#^ref-4|[4]]], [[#^ref-14|[14]]]. For instance, HGB has been shown to achieve high F1 scores in predicting 7-point TSV scales, enabling more precise adaptive control [[#^ref-14|[14]]].
- **Sequential and Neural Modeling**: Architectures like Attention-based Long Short-Term Memory (LSTM) and Gated Recurrent Units (GRU) are utilized to capture the temporal dependencies in occupancy and environmental data, providing accurate forecasts for proactive adjustment [[#^ref-9|[9]]], [[#^ref-15|[15]]], [[#^ref-40|[40]]].

### 2.4 Intelligent and Hybrid Control Frameworks
Intelligent systems combine multiple computational intelligence techniques to manage uncertainty and multi-objective trade-offs.
- **Fuzzy Logic Control**: Fuzzy inference systems handle the vagueness and non-linearity of human comfort preferences using "if-then" rules [[#^ref-12|[12]]], [[#^ref-21|[21]]]. They are often integrated with other controllers (e.g., Adaptive Fuzzy Neural Networks) to provide robust management in uncertain environments [[#^ref-9|[9]]], [[#^ref-13|[13]]].
- **Swarm Intelligence**: Algorithms like Particle Swarm Optimization (PSO) and Ant Colony Optimization are employed to optimize the parameters of HVAC systems and fine-tune control strategies for maximum efficiency [[#^ref-7|[7]]], [[#^ref-42|[42]]].
- **Hybrid Systems**: These frameworks integrate different paradigms, such as combining MPC for high-level supervisory control with RL for local adaptive tuning, to leverage the strengths of both model-based and model-free approaches [[#^ref-16|[16]]], [[#^ref-53|[53]]].

## 3. Technological Infrastructure and Architectures
The deployment of advanced HVAC control is supported by a sophisticated layer of hardware and software infrastructure [[#^ref-26|[26]]], [[#^ref-38|[38]]].

### 3.1 Advanced Sensing and IoT Integration
The Internet of Things (IoT) provides the critical data feed for smart building operations [[#^ref-23|[23]]], [[#^ref-56|[56]]].
- **Sensor Modalities**: Beyond standard temperature and humidity sensors, modern smart buildings employ CO2 sensors, air quality monitors, and smart meters to track real-time environmental and energy variables [[#^ref-10|[10]]], [[#^ref-23|[23]]].
- **Personalized Sensing**: Wearable sensors (e.g., Microsoft Band 2, wireless wristbands) and smartphone applications allow for the collection of physiological data and direct user feedback, facilitating "human-in-the-loop" control [[#^ref-5|[5]]], [[#^ref-19|[19]]], [[#^ref-24|[24]]].
- **Protocols**: Data is transmitted using a variety of protocols, from legacy industrial standards like BACnet and Modbus to modern IoT protocols like MQTT and 5G, ensuring low-latency communication across distributed networks [[#^ref-10|[10]]], [[#^ref-11|[11]]], [[#^ref-13|[13]]].

### 3.2 Human Activity Recognition and Occupancy Detection
Accurate occupancy detection is vital for minimizing energy waste in unoccupied spaces [[#^ref-33|[33]]], [[#^ref-58|[58]]].
- **Occupant Tracking**: Advanced systems utilize Passive Infrared (PIR) sensors, RFID tags, and Bluetooth Low Energy (BLE) for basic localization [[#^ref-24|[24]]], [[#^ref-43|[43]]].
- **Vision-Based Systems**: High-fidelity tracking is achieved through computer vision frameworks using RGB, CCTV, and long-wave infrared (LWIR) thermal cameras [[#^ref-24|[24]]]. State-of-the-art AI models like YOLO (You Only Look Once) and various Convolutional Neural Networks (CNNs) (e.g., R-CNN, Mask R-CNN, ResNet-50) are deployed for real-time human activity monitoring and clothing level estimation [[#^ref-24|[24]]].
- **LLM and AR Integration**: Emerging research explores the use of Large Language Models (LLMs) to allow occupants to interact with HVAC systems via natural language, and Augmented Reality (AR) to visualize indoor environmental quality in real-time [[#^ref-8|[8]]].

### 3.3 Computational Platforms and Software Frameworks
The processing requirements of smart building algorithms are distributed across edge and cloud layers [[#^ref-45|[45]]], [[#^ref-46|[46]]].
- **Edge Computing**: Lightweight devices like Raspberry Pi, Jetson Nano, and Arduino Nano handle local data acquisition, pre-processing, and real-time execution of control logic [[#^ref-9|[9]]], [[#^ref-10|[10]]], [[#^ref-11|[11]]].
- **Cloud Computing**: Computationally heavy tasks, such as training deep learning models or running large-scale MPC optimizations, are offloaded to cloud servers equipped with powerful GPUs (e.g., NVIDIA A100) [[#^ref-11|[11]]], [[#^ref-13|[13]]], [[#^ref-22|[22]]].
- **Software Stack**: Development and deployment rely on a diverse software ecosystem, including MATLAB/Simulink for modeling, Python libraries (TensorFlow, PyTorch, scikit-learn) for AI, and IoT platforms like ThingsBoard and Apache Kafka for data streaming and storage [[#^ref-9|[9]]], [[#^ref-10|[10]]], [[#^ref-13|[13]]], [[#^ref-24|[24]]].

## 4. Findings and Comparative Analysis
The literature review indicates several key findings regarding the performance of smart HVAC systems:
- **Efficiency Gains**: Advanced control strategies consistently deliver energy savings of 20% to 30% over traditional scheduling and PID methods [[#^ref-20|[20]]], [[#^ref-33|[33]]].
- **Comfort Optimization**: Data-driven models for PMV and TSV prediction significantly reduce the "discomfort hours" experienced by occupants compared to static setpoint management [[#^ref-4|[4]]], [[#^ref-14|[14]]], [[#^ref-49|[49]]].
- **System Resilience**: Model-free approaches like DRL show higher adaptability to changing building dynamics and sensor failures, although they require significant initial training periods [[#^ref-18|[18]]], [[#^ref-50|[50]]].
- **Load Flexibility**: Smart building systems facilitate participation in demand response programs, allowing buildings to act as flexible loads that support grid stability [[#^ref-39|[39]]], [[#^ref-54|[54]]].

## 5. Limitations of the Evidence
Despite the promising results, several limitations hinder the widespread implementation of advanced HVAC systems:
- **High Complexity and Initial Cost**: The requirement for extensive sensor networks and specialized engineering knowledge for model development poses a significant financial barrier, particularly for retrofitting existing buildings [[#^ref-36|[36]]], [[#^ref-37|[37]]].
- **Data Dependency and Quality**: Many learning-based methods are sensitive to data quality and require large historical datasets, which are often unavailable or incomplete [[#^ref-57|[57]]], [[#^ref-60|[60]]].
- **Interoperability and Standardization**: The lack of standardized communication between diverse IoT devices and legacy BMS hardware complicates system integration [[#^ref-10|[10]]], [[#^ref-64|[64]]].
- **Human Factors and Privacy**: Automated systems can sometimes conflict with occupant preferences, and the use of cameras and wearables for tracking raises significant privacy and security concerns [[#^ref-30|[30]]], [[#^ref-63|[63]]].

## 6. Research Gaps and Future Directions
The analysis identifies several avenues for future research to enhance the efficacy of smart building systems:
- **Scalable and Generalizable Models**: Future work should focus on developing AI models that can be easily transferred across different building types without extensive re-training or re-modeling [[#^ref-18|[18]]], [[#^ref-29|[29]]].
- **Fairness and Ethics in Automation**: There is a growing need to incorporate ethical considerations into climate control systems to ensure fair treatment of all occupants and transparent decision-making [[#^ref-25|[25]]].
- **Cyber-Physical Security**: As buildings become increasingly networked, robust defense mechanisms against cyber-attacks on HVAC infrastructure are essential [[#^ref-39|[39]]], [[#^ref-59|[59]]].
- **Digital Twins and Lifecycle Management**: Integrating Digital Twins with real-time HVAC control could optimize building performance throughout its entire lifecycle, from design to decommissioning [[#^ref-15|[15]]], [[#^ref-61|[61]]].
- **Grid Integration and Smart Cities**: Research should continue to explore the role of smart buildings as active nodes in the smart energy grid, contributing to the broader stability and sustainability of urban energy systems [[#^ref-35|[35]]], [[#^ref-62|[62]]].

## 7. Conclusion
The transition from traditional HVAC management to intelligent, data-driven building automation is a critical step toward achieving global energy efficiency and sustainability goals. This review has categorized the diverse landscape of control strategies, from the foundational PID logic to the cutting-edge DRL and MPC frameworks. While the potential for significant energy savings and improved occupant comfort is clear, the path to large-scale adoption requires addressing current challenges in model complexity, data quality, and system interoperability. By focusing on scalable, ethical, and secure technologies, the next generation of smart buildings will not only provide optimized indoor environments but also serve as vital assets in the evolving smart energy ecosystem.

---
**References**
*The references are rendered automatically by the system based on the provided citation keys.*

## References

[1]P. Michailidis, I. Michailidis, F. Minelli, H. H. Çoban, and E. B. Kosmatopoulos, “Model Predictive Control for Smart Buildings: Applications and Innovations in Energy Management,” Buildings, vol. 15, no. 18, pp. 3298–3298, Sept. 2025, doi: [10.3390/buildings15183298](https://doi.org/10.3390/buildings15183298). ^ref-1

[2]T. Wei, X. Chen, X. Li, and Q. Zhu, “Model-based and data-driven approaches for building automation and control,” p. 26, Nov. 2018, doi: [10.1145/3240765.3243485](https://doi.org/10.1145/3240765.3243485). ^ref-2

[3]V. Sharma and V. Mistry, “HVAC Load Prediction and Energy Saving Strategies in Building Automation,” Apr. 2024, doi: [10.5281/zenodo.11080079](https://doi.org/10.5281/zenodo.11080079). ^ref-3

[4]Y. Boutahri and A. Tilioua, “Machine learning-based predictive model for thermal comfort and energy optimization in smart buildings,” Results in engineering, June 2024, doi: [10.1016/j.rineng.2024.102148](https://doi.org/10.1016/j.rineng.2024.102148). ^ref-4

[5]W. Hu, “Transforming thermal comfort model and control in the tropics : a machine-learning approach,” Jan. 2020, doi: [10.32657/10356/141578](https://doi.org/10.32657/10356/141578). ^ref-5

[6]M. Royapoor, A. Antony, and T. Roskilly, “A review of building climate and plant controls, and a survey of industry perspectives,” Energy and Buildings, vol. 158, pp. 453–465, Jan. 2018, doi: [10.1016/J.ENBUILD.2017.10.022](https://doi.org/10.1016/J.ENBUILD.2017.10.022). ^ref-6

[7]I. V. Kanna et al., “Swarm intelligence for energy-efficient heating, ventilation, and air conditioning (HVAC) systems: A case study in smart buildings,” Case Studies in Thermal Engineering, Aug. 2025, doi: [10.1016/j.csite.2025.106823](https://doi.org/10.1016/j.csite.2025.106823). ^ref-7

[8]M. Mohammadi, O. Poudel, R. H. Assaad, M. Awada, and G. Assaf, “An Intelligent Cyber-Physical System Integrating Large Language Models (LLMs), IoT Wireless Sensor Networks, and Augmented Reality (AR) for Real-Time Indoor Environmental Quality Improvement and Automated HVAC Control in Smart Buildings,” pp. 980–989, Jan. 2026, doi: [10.1061/9780784486436.105](https://doi.org/10.1061/9780784486436.105). ^ref-8

[9]A. Kharbouch et al., “Internet-of-Things Based Hardware-in-the-Loop Framework for Model-Predictive-Control of Smart Building Ventilation,” Sensors, vol. 22, no. 20, pp. 7978–7978, Oct. 2022, doi: [10.3390/s22207978](https://doi.org/10.3390/s22207978). ^ref-9

[10]Y. M. Wijaya and F. Pasila, “AI-Driven Smart HVAC &amp; Building Automation in Asia: A Revolution in Energy Efficiency and ComfortInsinyur, Universitas Kristen Petra,” Jurnal Dimensi Insinyur Profesional, vol. 3, no. 2, pp. 32–39, Sept. 2025, doi: [10.9744/jdip.3.2.32-39](https://doi.org/10.9744/jdip.3.2.32-39). ^ref-10

[11]“IoT-Enabled Data-Driven Optimization of Dynamic Thermal Loads for Low-Energy Buildings,” International Journal of Advanced Computer Science and Applications, vol. 16, no. 10, Jan. 2025, doi: [10.14569/ijacsa.2025.0161004](https://doi.org/10.14569/ijacsa.2025.0161004). ^ref-11

[12]“Nonlinear Integrated Fuzzy Modeling to Predict Dynamic Occupant Environment Comfort for Optimized Sustainability,” Scientific Programming, vol. 2022, pp. 1–13, June 2022, doi: [10.1155/2022/4208945](https://doi.org/10.1155/2022/4208945). ^ref-12

[13]G. Serale, M. Fiorentini, A. Capozzoli, D. Bernardini, and A. Bemporad, “Model Predictive Control (MPC) for Enhancing Building and HVAC System Energy Efficiency: Problem Formulation, Applications and Opportunities,” Energies, vol. 11, no. 3, p. 631, Mar. 2018, doi: [10.3390/EN11030631](https://doi.org/10.3390/EN11030631). ^ref-13

[14]M. K. Erdem, O. Gökalp, and G. Calis, “Ensemble machine learning algorithms for thermal comfort prediction in HVAC systems of smart buildings,” Dec. 2025, doi: [10.31462/jcemi.2025.04346379](https://doi.org/10.31462/jcemi.2025.04346379). ^ref-14

[15]A. Almadhor et al., “Digital twin based deep learning framework for personalized thermal comfort prediction and energy efficient operation in smart buildings,” Dental science reports, July 2025, doi: [10.1038/s41598-025-10086-y](https://doi.org/10.1038/s41598-025-10086-y). ^ref-15

[16]J. Felez, “Intelligent HVAC Control in Residential Buildings: A System-atic Review of Advanced Techniques and AI Applications,” Jan. 2026, doi: [10.5281/zenodo.18171660](https://doi.org/10.5281/zenodo.18171660). ^ref-16

[17]M. K. Pasupuleti, “Model Predictive Control for Smart HVAC Systems in Green Buildings,” vol. 05, no. 06, pp. 1–11, June 2025, doi: [10.62311/nesx/rphcrefcs1](https://doi.org/10.62311/nesx/rphcrefcs1). ^ref-17

[18]E. S. Cardoso, “Advanced energy management strategies for HVAC systems in smart buildings,” Dec. 2019. ^ref-18

[19]“Data-driven based HVAC optimisation approaches: A Systematic Literature Review,” Journal of building engineering, vol. 46, pp. 103678–103678, Apr. 2022, doi: [10.1016/j.jobe.2021.103678](https://doi.org/10.1016/j.jobe.2021.103678). ^ref-19

[20]C. Petrie, S. Gupta, V. Rao, and B. Nutter, “Energy Efficient Control Methods of HVAC Systems for Smart Campus,” pp. 133–136, Apr. 2018, doi: [10.1109/GREENTECH.2018.00032](https://doi.org/10.1109/GREENTECH.2018.00032). ^ref-20

[21]J. Aguilar, A. Garces-Jimenez, N. Gallego-Salvador, J. A. G. de Mesa, J. M. Gómez-Pulido, and Á. J. García-Tejedor, “Autonomic Management Architecture for Multi-HVAC Systems in Smart Buildings,” IEEE Access, vol. 7, pp. 123402–123415, Aug. 2019, doi: [10.1109/ACCESS.2019.2937639](https://doi.org/10.1109/ACCESS.2019.2937639). ^ref-21

[22]X. Zhang, M. Pipattanasomporn, T. Chen, and S. Rahman, “An IoT-Based Thermal Model Learning Framework for Smart Buildings,” IEEE Internet of Things Journal, vol. 7, no. 1, pp. 518–527, Jan. 2020, doi: [10.1109/JIOT.2019.2951106](https://doi.org/10.1109/JIOT.2019.2951106). ^ref-22

[23]A. Kaligambe, G. Fujita, and T. Keisuke, “Estimation of Unmeasured Room Temperature, Relative Humidity, and CO2 Concentrations for a Smart Building Using Machine Learning and Exploratory Data Analysis,” Energies, vol. 15, no. 12, pp. 4213–4213, June 2022, doi: [10.3390/en15124213](https://doi.org/10.3390/en15124213). ^ref-23

[24]A. Borodinecs, J. Zemitis, and A. Palcikovskis, “HVAC System Control Solutions Based on Modern IT Technologies: A Review Article,” Energies, vol. 15, no. 18, pp. 6726–6726, Sept. 2022, doi: [10.3390/en15186726](https://doi.org/10.3390/en15186726). ^ref-24

[25]“Emma - the ethical multimodal, modeling and adaptive ai system for fairness in building tenant comfort,” Issues in information systems, Jan. 2022, doi: [10.48009/3_iis_2022_123](https://doi.org/10.48009/3_iis_2022_123). ^ref-25

[26]L. Akbulut et al., “A Systematic Review of Building Energy Management Systems (BEMSs): Sensors, IoT, and AI Integration,” Energies, Dec. 2025, doi: [10.3390/en18246522](https://doi.org/10.3390/en18246522). ^ref-26

[27]R. Aazami, M. Moradi, M. Shirkhani, A. Harrison, S. F. Al‐Gahtani, and Z. M. S. Elbarbary, “Technical Analysis of Comfort and Energy Consumption in Smart Buildings with Three Levels of Automation: Scheduling, Smart Sensors, and IoT,” IEEE Access, pp. 1–1, Jan. 2025, doi: [10.1109/access.2025.3526858](https://doi.org/10.1109/access.2025.3526858). ^ref-27

[28]R. Carli, G. Cavone, S. B. Othman, and M. Dotoli, “IoT Based Architecture for Model Predictive Control of HVAC Systems in Smart Buildings.,” Sensors, vol. 20, no. 3, p. 781, Jan. 2020, doi: [10.3390/S20030781](https://doi.org/10.3390/S20030781). ^ref-28

[29]R. Charmika, R. Navya, C. Vijay, G. Madhusudhan, L. Bhavana, and M. MAHESHKUMAR., “AI-Driven Automation for Green Buildings and Sustainable Agriculture: Enhancing Efficiency, Scalability, and Resource Management,” International research journal of innovations in engineering and technology, vol. 09, no. Special Issue, pp. 97–103, Jan. 2025, doi: [10.47001/irjiet/2025.inspire16](https://doi.org/10.47001/irjiet/2025.inspire16). ^ref-29

[30]Z. D. Belafi, Z. D. Belafi, T. Hong, and A. Reith, “Smart building management vs. intuitive human control—Lessons learnt from an office building in Hungary,” Building Simulation, vol. 10, no. 6, pp. 811–828, Apr. 2017, doi: [10.1007/S12273-017-0361-4](https://doi.org/10.1007/S12273-017-0361-4). ^ref-30

[31]N. Asim et al., “Sustainability of Heating, Ventilation and Air-Conditioning (HVAC) Systems in Buildings—An Overview,” International Journal of Environmental Research and Public Health, vol. 19, no. 2, pp. 1016–1016, Jan. 2022, doi: [10.3390/ijerph19021016](https://doi.org/10.3390/ijerph19021016). ^ref-31

[32]M. Ostadijafari, A. Dubey, Y. Liu, J. Shi, and N. Yu, “Smart Building Energy Management using Nonlinear Economic Model Predictive Control,” June 2019, doi: [10.1109/PESGM40551.2019.8973669](https://doi.org/10.1109/PESGM40551.2019.8973669). ^ref-32

[33]Y. Agarwal, B. Balaji, R. Gupta, J. Lyles, M. Wei, and T. Weng, “Occupancy-driven energy management for smart building automation,” pp. 1–6, Nov. 2010, doi: [10.1145/1878431.1878433](https://doi.org/10.1145/1878431.1878433). ^ref-33

[34]“Smart buildings: employing modern technology to create an integrated, data-driven, intelligent, self-optimizing, human-centered, building automation system,” Oct. 2022, doi: [10.25549/usctheses-c89-193100](https://doi.org/10.25549/usctheses-c89-193100). ^ref-34

[35]A. Parisio, M. Molinari, D. Varagnolo, and K. H. Johansson, “Energy Management Systems for Intelligent Buildings in Smart Grids,” no. 9783319684611, pp. 253–291, Jan. 2018, doi: [10.1007/978-3-319-68462-8_10](https://doi.org/10.1007/978-3-319-68462-8_10). ^ref-35

[36]T. M. Olatunde, A. C. Okwandu, D. O. Akande, and Z. Q. Sikhakhane, “Review of energy-efficient HVAC technologies for sustainable buildings,” International Journal of Science and Technology Research Archive, Apr. 2024, doi: [10.53771/ijstra.2024.6.2.0039](https://doi.org/10.53771/ijstra.2024.6.2.0039). ^ref-36

[37]W. M. T. Elamri and S. A. M. Abdasslam, “Review of energy-saving hvac systems for environmentally friendly structures,” International journal of engineering applied science and technology, Oct. 2025, doi: [10.33564/ijeast.2025.v10i06.008](https://doi.org/10.33564/ijeast.2025.v10i06.008). ^ref-37

[38]Y. V. S. Bharadwaj, Y. V. S. Bhageerath, and T. N. Gayathri, “Intelligent Energy Optimization in Buildings: The Synergistic Role of Smart Sensors, Building Automation Systems, and AI-Driven Analytics,” Apr. 2025, doi: [10.5281/zenodo.15152028](https://doi.org/10.5281/zenodo.15152028). ^ref-38

[39]J. Qi, Y.-J. Kim, C. Chen, X. Lu, and J. Wang, “Demand Response and Smart Buildings: A Survey of Control, Communication, and Cyber-Physical Security,” ACM Transactions on Cyber-Physical Systems, vol. 1, no. 4, p. 18, Oct. 2017, doi: [10.1145/3009972](https://doi.org/10.1145/3009972). ^ref-39

[40]Y. Huang, H. Miles, and P. Zhang, “A Sequential Modelling Approach for Indoor Temperature Prediction and Heating Control in Smart Buildings,” arXiv: Signal Processing, Sept. 2020. ^ref-40

[41]D. Kim, J. Lee, S. L. Do, P. J. Mago, K. H. Lee, and H. Cho, “Energy Modeling and Model Predictive Control for HVAC in Buildings: A Review of Current Research Trends,” Energies, vol. 15, no. 19, pp. 7231–7231, Oct. 2022, doi: [10.3390/en15197231](https://doi.org/10.3390/en15197231). ^ref-41

[42]M. W. Ahmad, M. Mourshed, B. Yuce, and Y. Rezgui, “Computational intelligence techniques for HVAC systems: a review,” Building Simulation, vol. 9, no. 4, pp. 359–398, Aug. 2016, doi: [10.1007/S12273-016-0285-4](https://doi.org/10.1007/S12273-016-0285-4). ^ref-42

[43]H. Park and S.-B. Rhee, “IoT-Based Smart Building Environment Service for Occupants’ Thermal Comfort,” Journal of Sensors, vol. 2018, no. 2018, pp. 1–10, May 2018, doi: [10.1155/2018/1757409](https://doi.org/10.1155/2018/1757409). ^ref-43

[44]Y. Dagdougui, A. Ouammi, and R. Benchrifa, “Energy Management-Based Predictive Controller for a Smart Building Powered by Renewable Energy,” Sustainability, vol. 12, no. 10, p. 4264, May 2020, doi: [10.3390/SU12104264](https://doi.org/10.3390/SU12104264). ^ref-44

[45]K. Lavingia and R. Mehta, “Information Retrieval and Data Analytics in Internet of Things : Current Perspective, Applications and Challenges,” Scalable Computing: Practice and Experience, vol. 23, no. 1, pp. 23–34, Apr. 2022, doi: [10.12694/scpe.v23i1.1969](https://doi.org/10.12694/scpe.v23i1.1969). ^ref-45

[46]J. Liu, “The Role of Machine Learning and the Internet of Things in Smart Buildings for Energy Efficiency,” Applied Sciences, vol. 12, no. 15, pp. 7882–7882, Aug. 2022, doi: [10.3390/app12157882](https://doi.org/10.3390/app12157882). ^ref-46

[47]P. A. Michailidis, I. Michailidis, D. Vamvakas, and E. Kosmatopoulos, “Model-Free HVAC Control in Buildings: A Review,” Energies, Oct. 2023, doi: [10.3390/en16207124](https://doi.org/10.3390/en16207124). ^ref-47

[48]J. D. Billanes, Z. Ma, and B. N. Jôrgensen, “Data-Driven Technologies for Energy Optimization in Smart Buildings: A Scoping Review,” Energies, vol. 18, no. 2, pp. 290–290, Jan. 2025, doi: [10.3390/en18020290](https://doi.org/10.3390/en18020290). ^ref-48

[49]M. Salem and R. M. Moussa, “A hybrid approach based on building physics and machine learning for thermal comfort prediction in smart buildings,” APJ, vol. 28, no. 3, Mar. 2023, doi: [10.54729/2789-8547.1203](https://doi.org/10.54729/2789-8547.1203). ^ref-49

[50]Um-e-Habiba, I. Ahmed, M. Asif, H. H. Alhelou, and M. A. M. Khalid, “A review on enhancing energy efficiency and adaptability through system integration for smart buildings,” Journal of building engineering, Apr. 2024, doi: [10.1016/j.jobe.2024.109354](https://doi.org/10.1016/j.jobe.2024.109354). ^ref-50

[51]K. A. Karoon, Y. Ibraheem, and P. Piroozfar, “Improving Energy Performance in Smart Buildings Through Information and Communication Technology: A State-of-The-Art Review,” Journal of Engineering and Sustainable Development, vol. 29, no. 3, pp. 297–309, May 2025, doi: [10.31272/jeasd.2550](https://doi.org/10.31272/jeasd.2550). ^ref-51

[52]L. Yu, S. Qin, M. Zhang, C. Shen, T. Jiang, and X. Guan, “A Review of Deep Reinforcement Learning for Smart Building Energy Management,” IEEE Internet of Things Journal, vol. 8, no. 15, pp. 12046–12063, Aug. 2021, doi: [10.1109/JIOT.2021.3078462](https://doi.org/10.1109/JIOT.2021.3078462). ^ref-52

[53]R. Rikame, M. Kr. Ranjan, M. Jadhav, and P. Bachhav, “A Hybrid Automata-Driven Machine Learning Framework for Real-Time Energy Optimization in Smart Buildings,” June 2025, doi: [10.1051/epjconf/202532801060/pdf](https://doi.org/10.1051/epjconf/202532801060/pdf). ^ref-53

[54]S. B. Thanikanti, D. Buvana, T.Yuvaraj, P. Mahmud, and B. Aljafari, “Smart Commercial Building Energy Management Incorporating Demand Response with Solar Energy Integration and Battery Electric Vehicle Support,” pp. 106–109, Aug. 2025, doi: [10.1109/iccpct65132.2025.11176781](https://doi.org/10.1109/iccpct65132.2025.11176781). ^ref-54

[55]M. V. Moreno et al., “Big data: the key to energy efficiency in smart buildings,” vol. 20, no. 5, pp. 1749–1762, May 2016, doi: [10.1007/S00500-015-1679-4](https://doi.org/10.1007/S00500-015-1679-4). ^ref-55

[56]K. M. Al-Obaidi, M. Hossain, N. A. M. Alduais, H. S. Al-Duais, H. Omrany, and A. Ghaffarianhoseini, “A Review of Using IoT for Energy Efficient Buildings and Cities: A Built Environment Perspective,” Energies, vol. 15, no. 16, pp. 5991–5991, Aug. 2022, doi: [10.3390/en15165991](https://doi.org/10.3390/en15165991). ^ref-56

[57]“Event Classification with Imbalanced and Missing Data for an Air-Handling Unit,” July 2022, doi: [10.1109/bdai56143.2022.9862614](https://doi.org/10.1109/bdai56143.2022.9862614). ^ref-57

[58]Y. Cardinale, “Occupant Activity Detection in Smart Buildings: A Review,” Social Science Research Network, June 2020, doi: [10.2139/SSRN.3671533](https://doi.org/10.2139/SSRN.3671533). ^ref-58

[59]R. Elsayed, M. I. Ismail, A. F. Ashour, H. A. Sakr, M. I. Ibrahem, and M. Fouda, “A Review of Smart Building Management Systems: CPS Applications for Energy-Efficient Monitoring and Control,” pp. 1–6, Sept. 2025, doi: [10.1109/aibthings66987.2025.11296174](https://doi.org/10.1109/aibthings66987.2025.11296174). ^ref-59

[60]D. Djenouri, R. Laidi, Y. Djenouri, and I. Balasingham, “Machine Learning for Smart Building Applications: Review and Taxonomy,” ACM Computing Surveys, vol. 52, no. 2, pp. 1–36, Mar. 2019, doi: [10.1145/3311950](https://doi.org/10.1145/3311950). ^ref-60

[61]S. Kundu, “Facility Management in the Age of IoT and Digital Twins: AI-Driven Optimization for Smart Buildings,” Mar. 2025, doi: [10.5281/zenodo.15087198](https://doi.org/10.5281/zenodo.15087198). ^ref-61

[62]V. Vahidinasab, C. Ardalan, B. Mohammadi-Ivatloo, D. Giaouris, and S. Walker, “Active Building as an Energy System: Concept, Challenges, and Outlook,” IEEE Access, vol. 9, pp. 58009–58024, Apr. 2021, doi: [10.1109/ACCESS.2021.3073087](https://doi.org/10.1109/ACCESS.2021.3073087). ^ref-62

[63]E. O. Alohan, A. K. Oyetunji, C. V. Amaechi, E. C. Dike, and P. E. Chima, “An Agreement Analysis on the Perception of Property Stakeholders for the Acceptability of Smart Buildings in the Nigerian Built Environment,” Buildings, vol. 13, no. 7, pp. 1620–1620, June 2023, doi: [10.3390/buildings13071620](https://doi.org/10.3390/buildings13071620). ^ref-63

[64]F. A. Ghansah, D.-G. Owusu-Manu, J. Ayarkwa, A. Darko, D. J. Edwards, and D. J. Edwards, “Underlying Indicators For Measuring Smartness Of Buildings In The Construction Industry,” Aug. 2020, doi: [10.1108/SASBE-05-2020-0061](https://doi.org/10.1108/SASBE-05-2020-0061). ^ref-64

# HVAC and Smart-Building Approaches: Traditional-to-Modern Comparison

## How to read this table

The approaches are ordered from **basic, reactive control** to **advanced, predictive, adaptive, and autonomous systems**. The rows are not all mutually exclusive: for example, a smart-building deployment may combine PID loops, occupancy sensing, MPC, machine learning, IoT communications, and a digital twin. The table therefore distinguishes between **control logic**, **optimization methods**, and **enabling architectures**.

| Evolution level | Approach | Main operating principle | Typical inputs | Main strengths | Main limitations | Relative maturity in HVAC practice | Representative literature |
|---|---|---|---|---|---|---|---|
| 1 | Manual/operator control | A facility operator changes setpoints, schedules, dampers, or equipment states based on observation and experience. | Local measurements, alarms, occupant feedback | Simple to deploy; flexible for unusual situations; little algorithmic infrastructure required | Reactive; inconsistent; difficult to scale; strongly dependent on operator skill; limited continuous optimization | Very high as a fallback or legacy mode | Belafi et al.; Royapoor et al. [[#^ref-6|\[6]], [[#^ref-30|30\]]] |
| 2 | Fixed scheduling / time-clock control | HVAC equipment follows predefined start/stop times and seasonal schedules. | Clock time, calendar, season, simple occupancy assumptions | Low cost; easy to configure; predictable operation | Cannot respond well to variable occupancy, weather, internal loads, or equipment faults; may condition empty spaces | Very high | Petrie et al.; Aazami et al. [[#^ref-20|\[20]], [[#^ref-27|27\]]] |
| 3 | On/off thermostat control | Heating or cooling switches on when a measured variable crosses a threshold and switches off after reaching a target. | Zone temperature; upper and lower thresholds | Extremely simple; inexpensive; robust; easy to understand | Temperature oscillation; poor coordination among zones; limited energy optimization; no anticipation of future conditions | Very high | Borodinecs et al.; Royapoor et al. [[#^ref-6|\[6]], [[#^ref-24|24\]]] |
| 4 | Hysteresis / dead-band control | On/off operation uses separate switching thresholds to prevent rapid cycling. | Zone temperature; dead-band limits | Reduces actuator chattering and equipment cycling; simple implementation | Still reactive; does not optimize energy, comfort, or system-wide interactions | Very high | Borodinecs et al.; Asim et al. [[#^ref-24|\[24]], [[#^ref-31|31\]]] |
| 5 | PI/PID control | A feedback controller adjusts a valve, damper, fan, or actuator using present error and, for PID, accumulated and rate-of-change error. | Temperature, pressure, humidity, airflow, supply-air conditions | Fast response; widely understood; inexpensive; effective for stable single-loop processes | Requires tuning; performance degrades under changing dynamics, disturbances, nonlinearities, and interacting zones; does not naturally optimize multiple objectives | Very high at the equipment-loop level | Royapoor et al.; Borodinecs et al. [[#^ref-6|\[6]], [[#^ref-24|24\]]] |
| 6 | Setpoint reset / supervisory control | A higher-level controller resets supply-air temperature, static pressure, chilled-water temperature, or zone setpoints according to load or operating conditions. | Zone demand, outdoor air, equipment status, load indicators | Improves coordination above local loops; can reduce fan, pump, and plant energy | Usually depends on heuristics or simplified models; performance depends on sensor quality and reset rules | High | Royapoor et al.; Asim et al. [[#^ref-6|\[6]], [[#^ref-31|31\]]] |
| 7 | Rule-based control | Expert-defined IF–THEN rules map measured conditions to HVAC actions. | Temperature, humidity, CO2, occupancy, schedules, alarms | Transparent; easy to audit; can encode operational knowledge; works without extensive training data | Rule conflicts, rule explosion, maintenance burden, weak generalization to unseen conditions | High | Wei et al.; Aguilar et al. [[#^ref-2|\[2]], [[#^ref-21|21\]]] |
| 8 | Fuzzy-logic control | Linguistic variables such as “slightly warm” or “high occupancy” are converted into graded control actions through membership functions and rules. | Temperature error, humidity, occupancy, comfort indicators | Handles uncertainty and nonlinear behavior; does not require an exact plant model; interpretable relative to black-box AI | Requires expert design and tuning; scaling rules to many zones can be difficult; validation may be incomplete | Medium to high | Ahmad et al.; nonlinear fuzzy comfort modeling studies [[#^ref-12|\[12]], [[#^ref-42|42\]]] |
| 9 | Occupancy-driven control | HVAC operation adapts to detected, estimated, or scheduled occupancy rather than assuming a fixed schedule. | Motion, CO2, Wi-Fi, access data, cameras, wearables, schedules | Avoids conditioning unoccupied areas; aligns operation with actual use; supports zone-level control | Occupancy detection may be noisy or privacy-sensitive; prediction errors can cause discomfort or unnecessary switching | High and increasingly common in smart buildings | Agarwal et al.; Park and Rhee; Cardinale [[#^ref-33|\[33]], [[#^ref-43|43]], [[#^ref-58|58\]]] |
| 10 | Demand-controlled ventilation (DCV) | Outdoor-airflow rate is adjusted according to occupancy or indoor-air-quality indicators, commonly CO2 and related measurements. | CO2, occupancy, airflow, indoor air quality, outdoor conditions | Can reduce ventilation-related heating and cooling loads while maintaining air quality | Sensor calibration, pollutant diversity, minimum ventilation requirements, and transient response must be managed | High | Asim et al.; Park and Rhee [[#^ref-31|\[31]], [[#^ref-43|43\]]] |
| 11 | Fault detection and diagnostics (FDD) | Rules, statistical methods, or machine learning identify abnormal equipment behavior and possible faults. | Sensors, alarms, trends, equipment states, residuals | Detects degradation and sensor/equipment problems; can support predictive maintenance and safer control | Requires reliable data, fault labels or residual models, and integration with maintenance workflows | Medium to high | Event-classification and smart-BMS studies [[#^ref-57|\[57]], [[#^ref-59|59\]]] |
| 12 | Physics-based building/HVAC modeling | Thermal and equipment behavior are represented using physical equations, simulation models, or reduced-order representations. | Weather, building envelope, equipment characteristics, internal gains, schedules | Interpretable; supports simulation, what-if analysis, design, and predictive control; can operate with limited historical data | Model development and calibration are time-consuming; model mismatch can reduce control quality; high-fidelity models may be computationally expensive | High for design and advanced control; lower for fully automated model creation | Serale et al.; Kim et al. [[#^ref-13|\[13]], [[#^ref-41|41\]]] |
| 13 | Data-driven system identification / grey-box modeling | A simplified physical structure is combined with parameters learned from measured building data. | Historical and real-time sensor data; simplified physical assumptions | Balances interpretability and adaptability; often less expensive than detailed modeling; useful for online updates | Needs informative data; parameter estimation and changing operating conditions remain challenging | High in research and growing in deployment | Wei et al.; Zhang et al. [[#^ref-2|\[2]], [[#^ref-22|22\]]] |
| 14 | Statistical load and temperature forecasting | Regression, time-series, or sequential models predict future loads, temperatures, or energy use. | Historical loads, weather forecasts, occupancy, calendar variables | Supports proactive scheduling and control; comparatively simple compared with deep learning | Forecast errors propagate into control decisions; performance can vary across seasons and buildings | High | Sharma and Mistry; Huang et al. [[#^ref-3|\[3]], [[#^ref-40|40\]]] |
| 15 | Conventional supervised machine learning | Algorithms such as regression, support-vector methods, decision trees, or nearest-neighbor methods learn mappings from building data to loads, temperatures, comfort, or control variables. | Sensor histories, weather, occupancy, equipment states | Captures nonlinear relationships; often effective with moderate datasets; useful for prediction and classification | Data dependence; limited extrapolation; retraining and explainability challenges; prediction is not automatically control | Medium to high | Djenouri et al.; Liu [[#^ref-46|\[46]], [[#^ref-60|60\]]] |
| 16 | Ensemble machine learning | Multiple models, such as random forests, boosted trees, or stacked learners, are combined to improve prediction robustness. | Multivariate building and occupant data | Often strong predictive accuracy; handles nonlinearities and heterogeneous features; can estimate variable importance | Higher computational and maintenance burden than a single model; still dependent on representative training data | Medium and growing | Ensemble thermal-comfort studies; Djenouri et al. [[#^ref-14|\[14]], [[#^ref-60|60\]]] |
| 17 | Artificial neural networks / deep learning | Neural networks learn complex nonlinear representations for load forecasting, state estimation, comfort prediction, or control support. | Large time-series datasets, images, sensor streams, weather, occupancy | Strong function approximation; supports multimodal and high-dimensional data; can model complex dynamics | Data-hungry; opaque; vulnerable to distribution shift; training and validation can be costly; predictions do not guarantee safe control | Medium to high in research; selective deployment | Djenouri et al.; Liu; Billanes et al. [[#^ref-46|\[46]], [[#^ref-48|48]], [[#^ref-60|60\]]] |
| 18 | Thermal-comfort prediction models | Models estimate occupant comfort or discomfort from environmental, physiological, behavioral, and contextual variables. | Temperature, humidity, air speed, clothing/activity assumptions, occupant feedback, physiological or behavioral data | Enables comfort-aware control rather than temperature-only control; supports personalization | Comfort is subjective and heterogeneous; labels can be sparse; privacy and fairness issues arise with personal data | Medium | Hu; Boutahri and Tilioua; Salem and Moussa [[#^ref-4|\[4]], [[#^ref-5|5]], [[#^ref-49|49\]]] |
| 19 | Adaptive / personalized comfort control | Control targets are adjusted to individual, group, or context-specific preferences rather than one fixed comfort band. | Occupant feedback, personal profiles, environmental data, activity, location | Can improve perceived comfort and reduce over-conditioning; supports human-centered operation | Preference learning, privacy, fairness, occupant participation, and conflicting preferences are difficult to manage | Emerging to medium | Hu; comfort-personalization and ethical AI studies [[#^ref-5|\[5]], [[#^ref-15|15]], [[#^ref-25|25\]]] |
| 20 | Model Predictive Control (MPC) | A model predicts future building behavior over a moving horizon, optimizes control actions, applies the first action, and repeats the process. | Forecast weather, occupancy, loads, zone states, equipment constraints, energy prices | Proactive; handles multivariable coupling, constraints, comfort, and energy objectives; naturally supports coordination | Requires a model, forecasts, computational resources, commissioning, and reliable measurements; model mismatch matters | High in research and increasing in advanced deployments | Serale et al.; Carli et al.; Kim et al. [[#^ref-13|\[13]], [[#^ref-28|28]], [[#^ref-41|41\]]] |
| 21 | Nonlinear MPC | MPC uses nonlinear building, equipment, or comfort models to represent nonlinear behavior more accurately. | Nonlinear state estimates, forecasts, equipment constraints, prices | More expressive than linear MPC; can represent nonlinear plant and comfort relationships | Greater computational burden; local optima and solver reliability can be concerns; calibration is harder | Medium | Ostadijafari et al.; Kim et al. [[#^ref-32|\[32]], [[#^ref-41|41\]]] |
| 22 | Economic MPC | MPC directly optimizes operating cost, energy price, carbon, demand charges, or other economic objectives while enforcing comfort and equipment constraints. | Energy prices, carbon signals, forecasts, comfort bounds, equipment states | Connects HVAC control to operating cost and grid conditions; supports multi-objective trade-offs | Requires price/carbon signals and reliable forecasts; objective design can conflict with occupant comfort | Medium to high | Ostadijafari et al.; Parisio et al.; Dagdougui et al. [[#^ref-32|\[32]], [[#^ref-35|35]], [[#^ref-44|44\]]] |
| 23 | Robust / stochastic MPC | MPC explicitly accounts for uncertainty in weather, occupancy, forecasts, and model parameters. | Forecast distributions, uncertainty bounds, disturbance scenarios | Improves resilience to uncertainty and reduces risk of constraint violations | More complex formulation; conservative solutions or high computational demand are possible | Medium and developing | MPC reviews and smart-building energy-management studies [[#^ref-1|\[1]], [[#^ref-13|13]], [[#^ref-41|41\]]] |
| 24 | Distributed / multi-zone MPC | Multiple controllers coordinate local zones or subsystems rather than relying on one centralized optimization problem. | Zone states, shared plant constraints, local forecasts, communication data | Scales to larger buildings; can improve modularity and fault isolation; supports multi-HVAC coordination | Communication delays, coordination design, inconsistent local objectives, and cybersecurity risks | Medium and developing | Aguilar et al.; Carli et al. [[#^ref-21|\[21]], [[#^ref-28|28\]]] |
| 25 | Metaheuristic optimization | Evolutionary, swarm, genetic, particle-swarm, or related search methods optimize schedules, setpoints, equipment combinations, or controller parameters. | Simulation outputs, measured performance, constraints, objective functions | Useful for nonconvex and discrete optimization; does not require gradient information | May require many evaluations; optimality is not guaranteed; online use can be difficult; computational cost can be high | Medium, mainly for design and supervisory optimization | Kanna et al.; Ahmad et al. [[#^ref-7|\[7]], [[#^ref-42|42\]]] |
| 26 | Hybrid physics–machine-learning control | Physical models provide structure, constraints, or priors while machine learning captures residuals, unknown dynamics, or occupant behavior. | Physics variables, sensor histories, forecasts, learned residuals | Combines interpretability and adaptability; can reduce data requirements; supports safer learning | Integration, calibration, uncertainty estimation, and stability guarantees remain challenging | Emerging to medium | Salem and Moussa; Wei et al.; Zhang et al. [[#^ref-2|\[2]], [[#^ref-22|22]], [[#^ref-49|49\]]] |
| 27 | Model-free reinforcement learning (RL) | An agent learns actions through interaction or data by maximizing cumulative reward rather than using an explicit plant model. | States, actions, rewards, constraints, historical or simulated experience | Can learn complex policies and adapt to nonlinear dynamics; avoids explicit model construction | Exploration can be unsafe; sample inefficient; reward design is difficult; transfer from simulation to real buildings is challenging | Emerging | Michailidis et al.; Yu et al. [[#^ref-47|\[47]], [[#^ref-52|52\]]] |
| 28 | Deep reinforcement learning (DRL) | Deep neural networks approximate policies or value functions for high-dimensional HVAC state and action spaces. | Multivariate sensor states, forecasts, rewards, simulation or operational data | Handles large state spaces and sequential decisions; supports nonlinear, multi-objective policies | Safety, explainability, training stability, sim-to-real transfer, data requirements, and constraint enforcement remain major barriers | Emerging; strong research activity | Yu et al.; Michailidis et al. [[#^ref-47|\[47]], [[#^ref-52|52\]]] |
| 29 | Multi-agent reinforcement learning | Several learning agents coordinate zones, air-handling units, chillers, or buildings through shared or local rewards. | Local observations, shared plant states, communication, reward signals | Suits distributed buildings and interacting subsystems; supports scalable coordination | Non-stationarity, communication requirements, reward conflict, and difficult validation | Emerging | Smart-building energy-management and distributed-control literature [[#^ref-21|\[21]], [[#^ref-52|52\]]] |
| 30 | IoT-enabled HVAC control | Networked sensors and actuators continuously collect and exchange data with HVAC controllers and building-management systems. | Temperature, humidity, CO2, occupancy, airflow, power, equipment status | Enables fine-grained monitoring, remote supervision, occupancy awareness, and data-driven control | Connectivity, interoperability, sensor drift, data quality, privacy, and cybersecurity risks | High as infrastructure; intelligence depends on the control layer | Park and Rhee; Carli et al.; Al-Obaidi et al. [[#^ref-28|\[28]], [[#^ref-43|43]], [[#^ref-56|56\]]] |
| 31 | Cyber-physical system (CPS) architecture | Physical HVAC processes are integrated with computation, communication, sensing, and feedback for closed-loop operation. | Physical measurements, network data, control commands, system models | Supports real-time automation, coordination, monitoring, and integration across building subsystems | Cybersecurity, timing, reliability, interoperability, and safety must be addressed jointly | High as a systems concept; deployment maturity varies | Aguilar et al.; Elsayed et al. [[#^ref-21|\[21]], [[#^ref-59|59\]]] |
| 32 | BEMS/BAS-integrated intelligent control | A building or energy-management system coordinates HVAC, lighting, meters, alarms, schedules, and other subsystems. | Multi-system sensor and equipment data; schedules; tariffs; alarms | Provides centralized monitoring, supervisory control, analytics, and integration | Legacy protocols, vendor lock-in, incomplete data access, and commissioning complexity | High | Wei et al.; Akbulut et al.; Borodinecs et al. [[#^ref-2|\[2]], [[#^ref-24|24]], [[#^ref-26|26\]]] |
| 33 | Edge computing for HVAC | Data processing and selected control decisions are performed near sensors and equipment rather than exclusively in a remote cloud. | Local sensor streams, local models, equipment states | Low latency; improved resilience during network outages; reduced data transfer; better privacy potential | Limited computational resources; distributed software maintenance; device heterogeneity | Medium and growing | IoT and smart-building architecture reviews [[#^ref-46|\[46]], [[#^ref-56|56\]]] |
| 34 | Cloud-based analytics and control | Building data are transmitted to remote computing infrastructure for storage, analytics, model training, optimization, or supervisory control. | Large historical datasets, multi-building data, remote telemetry | Scalable computation and storage; supports fleet-level analytics and model updates | Network dependence, latency, privacy, cybersecurity, and cloud costs | High for analytics; direct closed-loop control requires safeguards | Moreno et al.; Al-Obaidi et al. [[#^ref-55|\[55]], [[#^ref-56|56\]]] |
| 35 | Edge–cloud hybrid control | Time-critical control runs locally while training, historical analytics, optimization, or fleet coordination runs in the cloud. | Local real-time data plus cloud models and historical data | Balances latency, scalability, resilience, and computational power; suitable for large portfolios | Architecture and synchronization complexity; model/version governance is required | Emerging to medium | IoT, CPS, and smart-BEMS literature [[#^ref-21|\[21]], [[#^ref-46|46]], [[#^ref-56|56]], [[#^ref-59|59\]]] |
| 36 | Hardware-in-the-loop (HIL) control validation | Real controllers or equipment interfaces are tested against simulated building or plant dynamics before deployment. | Simulated states, real controller commands, equipment interfaces | Reduces deployment risk; tests timing, communication, and controller behavior under repeatable scenarios | Requires specialized testbeds and representative models; test coverage can be limited | Medium, especially for advanced MPC and research validation | Kharbouch et al. [[#^ref-9|[9]]] |
| 37 | Digital-twin-based control | A continuously updated digital representation of the building and HVAC plant supports monitoring, prediction, diagnosis, simulation, and optimization. | BIM/asset data, sensor streams, equipment models, historical data | Enables synchronized monitoring, what-if analysis, predictive maintenance, and advanced control | High implementation cost; model synchronization, data governance, interoperability, and validation are difficult | Emerging | Almadhor et al.; Kundu [[#^ref-15|\[15]], [[#^ref-61|61\]]] |
| 38 | Demand-response HVAC control | HVAC flexibility is shifted, curtailed, or preconditioned in response to grid signals, prices, demand limits, or carbon intensity while maintaining comfort. | Electricity prices, grid signals, forecasts, occupancy, comfort constraints | Converts buildings into flexible energy resources; reduces peak demand and can support renewable integration | Requires reliable communication, occupant acceptance, tariff/grid participation, and careful comfort management | Medium to high | Qi et al.; Parisio et al.; Vahidinasab et al. [[#^ref-35|\[35]], [[#^ref-39|39]], [[#^ref-62|62\]]] |
| 39 | Renewable-storage-EV coordinated control | HVAC is optimized jointly with solar generation, batteries, electric vehicles, and grid exchange. | Solar forecasts, battery state of charge, EV availability, prices, HVAC states | Enables whole-building energy optimization and increased renewable self-consumption | More coupled assets and constraints; requires broader metering, forecasting, and coordination | Emerging to medium | Dagdougui et al.; Thanikanti et al. [[#^ref-44|\[44]], [[#^ref-54|54\]]] |
| 40 | Multi-objective human-centered optimization | The controller jointly considers energy, cost, emissions, thermal comfort, indoor air quality, health, fairness, and occupant preferences. | Energy and environmental sensors, occupancy, comfort feedback, prices, carbon, preferences | Reflects real smart-building objectives rather than energy alone; supports balanced decisions | Objectives can conflict; weights and fairness criteria are difficult to define; occupant feedback may be sparse | Emerging | Boutahri and Tilioua; Emma; Aazami et al. [[#^ref-4|\[4]], [[#^ref-25|25]], [[#^ref-27|27\]]] |
| 41 | Explainable, ethical, and privacy-aware AI control | AI decisions are constrained or accompanied by explanations, privacy protections, fairness checks, and human override mechanisms. | Sensor data, occupant data, model explanations, privacy policies, comfort outcomes | Improves trust, governance, accountability, and acceptability of intelligent HVAC | Adds design and computational overhead; explainability does not by itself guarantee correctness or safety | Emerging | Emma; smart-building acceptability and AI-integration studies [[#^ref-25|\[25]], [[#^ref-63|63\]]] |
| 42 | Large-language-model or multimodal-agent HVAC supervision | A language or multimodal AI layer interprets operational context, user requests, alarms, and building data, then assists or supervises lower-level control systems. | Natural-language requests, sensor data, alarms, documents, images, structured building data | Flexible human interaction; can assist diagnosis, workflow orchestration, and high-level supervisory decisions | Hallucination, verification, cybersecurity, latency, privacy, and unsafe direct actuation require strict safeguards | Very emerging | Mohammadi et al. [[#^ref-8|[8]]] |

## Overall progression

| Stage | Dominant logic | Typical level of automation | Main objective | Main data requirement | Main unresolved issue |
|---|---|---|---|---|---|
| Traditional/basic | Reactive feedback, schedules, thresholds, and manually written rules | Equipment-loop or schedule-level automation | Maintain temperature and basic operation | Small number of local measurements | Inefficiency under changing occupancy and weather |
| Intermediate | Supervisory rules, occupancy response, forecasting, physical or grey-box models | Building-management and multi-zone coordination | Improve energy use while maintaining comfort | More sensors, equipment states, weather, and occupancy information | Model calibration, interoperability, and commissioning |
| Advanced predictive | MPC, economic MPC, robust MPC, and optimization | Proactive multi-variable control | Balance comfort, energy, cost, emissions, and constraints | Forecasts, models, prices, and system-wide measurements | Forecast/model uncertainty and computational complexity |
| Data-driven intelligent | Supervised ML, ensembles, deep learning, adaptive models, and comfort prediction | Adaptive prediction and decision support | Learn nonlinear behavior and personalize operation | Large, clean, representative datasets | Generalization, explainability, drift, and safe deployment |
| Autonomous/emerging | RL/DRL, digital twins, multi-agent control, multimodal agents, and human-centered AI | Self-optimizing or semi-autonomous operation | Coordinate building, occupant, and grid objectives | Continuous sensing, simulation, feedback, and governance data | Safety, trust, cybersecurity, privacy, interoperability, and real-world validation |

## Key comparison conclusions

1. **Traditional methods remain essential.** On/off, PID, schedules, and rule-based logic are still the foundation of reliable local HVAC operation; modern methods generally supervise or augment rather than eliminate them [[#^ref-6|\[6]], [[#^ref-24|24\]]].
2. **MPC is the main bridge between conventional automation and intelligent control.** It introduces prediction and explicit constraint handling while remaining more interpretable and easier to validate than many black-box learning policies [[#^ref-13|\[13]], [[#^ref-28|28]], [[#^ref-41|41\]]].
3. **Machine learning is strongest when used for prediction, estimation, diagnosis, or model enhancement.** Forecasting loads, occupancy, temperatures, and comfort can improve control, but a predictive model alone is not a complete HVAC control strategy [[#^ref-2|\[2]], [[#^ref-19|19]], [[#^ref-22|22]], [[#^ref-46|46\]]].
4. **Reinforcement learning and digital twins represent a shift toward autonomous adaptation.** Their promise is high, but safety, transfer from simulation to real buildings, data quality, and validation remain major barriers [[#^ref-15|\[15]], [[#^ref-47|47]], [[#^ref-52|52]], [[#^ref-61|61\]]].
5. **IoT, CPS, BEMS, edge/cloud, and digital twins are enabling layers rather than standalone control algorithms.** They provide sensing, communication, computation, integration, and synchronization for the control approaches above [[#^ref-21|\[21]], [[#^ref-28|28]], [[#^ref-46|46]], [[#^ref-56|56]], [[#^ref-59|59\]]].
6. **The modern objective is multi-objective and human-centered.** Energy minimization must be balanced with thermal comfort, indoor air quality, cost, carbon, grid flexibility, privacy, fairness, and occupant acceptance [[#^ref-4|\[4]], [[#^ref-25|25]], [[#^ref-27|27]], [[#^ref-39|39\]]].

## References

The bracketed citations refer to the numbered references in the source literature review, **Taxonomy and Literature Review of HVAC Control and Infrastructure in Smart Buildings**. The most frequently used sources in this comparison are:

- [[#^ref-2|[2]]] Wei, T., Chen, X., Li, X., & Zhu, Q. (2018). *Model-based and data-driven approaches for building automation and control*.
- [[#^ref-4|[4]]] Boutahri, Y., & Tilioua, A. (2024). *Machine learning-based predictive model for thermal comfort and energy optimization in smart buildings*.
- [[#^ref-6|[6]]] Royapoor, M., Antony, A., & Roskilly, T. (2018). *A review of building climate and plant controls, and a survey of industry perspectives*. Energy and Buildings.
- [[#^ref-13|[13]]] Serale, G., Fiorentini, M., Capozzoli, A., Bernardini, D., & Bemporad, A. (2018). *Model Predictive Control for Enhancing Building and HVAC System Energy Efficiency: Problem Formulation, Applications and Opportunities*. Energies.
- [[#^ref-15|[15]]] Almadhor, A., et al. (2025). *Digital twin based deep learning framework for personalized thermal comfort prediction and energy efficient operation in smart buildings*. Scientific Reports.
- [[#^ref-21|[21]]] Aguilar, J., et al. (2019). *Autonomic Management Architecture for Multi-HVAC Systems in Smart Buildings*. IEEE Access.
- [[#^ref-22|[22]]] Zhang, X., Pipattanasomporn, M., Chen, T., & Rahman, S. (2020). *An IoT-Based Thermal Model Learning Framework for Smart Buildings*. IEEE Internet of Things Journal.
- [[#^ref-24|[24]]] Borodinecs, A., Zemitis, J., & Palcikovskis, A. (2022). *HVAC System Control Solutions Based on Modern IT Technologies: A Review Article*. Energies.
- [[#^ref-28|[28]]] Carli, R., Cavone, G., Othman, S. B., & Dotoli, M. (2020). *IoT Based Architecture for Model Predictive Control of HVAC Systems in Smart Buildings*. Sensors.
- [[#^ref-39|[39]]] Qi, J., Kim, Y.-J., Chen, C., Lu, X., & Wang, J. (2017). *Demand Response and Smart Buildings: A Survey of Control, Communication, and Cyber-Physical Security*. ACM Transactions on Cyber-Physical Systems.
- [[#^ref-41|[41]]] Kim, D., et al. (2022). *Energy Modeling and Model Predictive Control for HVAC in Buildings: A Review of Current Research Trends*. Energies.
- [[#^ref-42|[42]]] Ahmad, M. W., Mourshed, M., Yuce, B., & Rezgui, Y. (2016). *Computational intelligence techniques for HVAC systems: a review*. Building Simulation.
- [[#^ref-46|[46]]] Liu, J. (2022). *The Role of Machine Learning and the Internet of Things in Smart Buildings for Energy Efficiency*. Applied Sciences.
- [[#^ref-47|[47]]] Michailidis, P. A., et al. (2023). *Model-Free HVAC Control in Buildings: A Review*. Energies.
- [[#^ref-52|[52]]] Yu, L., et al. (2021). *A Review of Deep Reinforcement Learning for Smart Building Energy Management*. IEEE Internet of Things Journal.
- [[#^ref-56|[56]]] Al-Obaidi, K. M., et al. (2022). *A Review of Using IoT for Energy Efficient Buildings and Cities: A Built Environment Perspective*. Energies.
- [[#^ref-60|[60]]] Djenouri, D., Laidi, R., Djenouri, Y., & Balasingham, I. (2019). *Machine Learning for Smart Building Applications: Review and Taxonomy*. ACM Computing Surveys.