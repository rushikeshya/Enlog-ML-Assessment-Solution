# Enlog-ML-Assessment-Solution

# Understanding and Identifying Air Conditioner Usage from Electrical Current Data

## Introduction
To better understand how electricity is used in a room, I analyzed a dataset containing one full day of electrical measurements. The dataset includes **5575 readings** with information about voltage, current, and timestamps. The **current column represents the total electrical consumption of the room**, meaning it includes the combined load from all appliances such as lights, fans, and possibly an air conditioner.

The goal of this analysis was to explore the data, understand the behavior of different electrical loads, and develop a logical way to **distinguish air conditioner (AC) usage from other household appliances**.

---

## Understanding the Electrical Data
Electricity consumption can be explained using basic electrical concepts. **Current (measured in amperes)** represents the flow of electricity used by appliances, while **voltage (measured in volts)** represents the electrical potential supplied to them. When these two values are combined, we can estimate the **power consumed by devices**, which helps identify appliances that use large amounts of electricity.

After examining the dataset, it became clear that **most of the current readings are very small**. Statistical analysis shows that **75% of the values are below 0.36 A**, which likely represents background electricity usage from small devices such as lights, fans, or electronics in standby mode.

However, while exploring the data further, I noticed that there are occasional moments where the current suddenly increases to **very high values, reaching up to 25 A**. These spikes are significantly different from the normal background consumption and indicate the operation of a **high-power appliance**.

---

## Air Conditioner Behavior
Air conditioners are among the largest electricity consumers in a typical room. Unlike small appliances, they usually operate in **cycles**. When the AC compressor starts, it causes a **sudden increase in current**, followed by a **stable period of high current while the compressor runs**, and then a **drop in current when the compressor turns off**.

This creates a recognizable pattern in the electrical signal:

- A sudden jump in current when the compressor starts  
- A steady high current while the AC runs  
- A drop when the compressor stops  

Other appliances behave differently. For example, lights and fans typically draw **small and steady currents**, while appliances like kettles or geysers may cause **short bursts of high current** but usually do not run continuously for long durations.

---

## Proposed Method to Isolate AC Usage
To separate air conditioner consumption from the total current signal, a simple statistical approach can be used. The dataset shows an **average current of about 1.78 A** with a **standard deviation of about 3.80 A**. Using these values, we can estimate a boundary that identifies unusually high current events.

Adding the mean and standard deviation gives a value close to **5–6 A**, which can serve as a reasonable threshold for detecting heavy electrical loads.

Using this idea, AC usage can be identified through two main conditions:

1. **Magnitude of current** – when the current exceeds approximately **5 A**, it indicates the presence of a high-power appliance.  
2. **Duration of usage** – if the current remains above this level for a longer continuous period, it is likely due to an air conditioner rather than short-duration appliances.

By combining these two signals—**high current level and sustained duration**—we can effectively isolate periods where the air conditioner is operating.

---

## Conclusion
Through statistical analysis and an understanding of appliance behavior, it becomes possible to identify patterns in the electrical signal that indicate air conditioner usage. Most of the time the room consumes only a small amount of electricity, representing normal background loads. Occasionally, large spikes in current reveal the operation of heavy appliances.

By applying a simple threshold and considering how long the current stays elevated, we can separate air conditioner activity from the total electrical consumption in a clear and logical way. This approach provides a practical foundation for preparing the data before building more advanced energy monitoring or machine learning systems.
