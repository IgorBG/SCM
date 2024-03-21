# Controlling the levels of stocks in business-units

## Versions: text - [pdf](https://docs.google.com/document/d/1PFvjcTjefLC5-4FEulmb9gtQe2zFbfxz56QSNRsgpJY/export?format=pdf), [html](https://docs.google.com/document/d/e/2PACX-1vSZM7a34OdUiPFmHq4VV2Rxv-ZepEOkEpM4944fERNSjgZcsJvjACqm9__JT1-cEkHxrQQAIq4OUJjd/pub), [gdoc](https://docs.google.com/document/d/1PFvjcTjefLC5-4FEulmb9gtQe2zFbfxz56QSNRsgpJY/edit?usp=sharing)

Stock level dynamics. Decisions on safety stock. Reorder point planning. Refilling the stocks in distribution centers. Inventory Management System.

## Tasks
The main tasks in inventory management are:
* When to put a new order for a future delivery: R =?
* What quantity should be in the order: Q =?
* Will we reserve a safety stock? Will this stock be consumable or should it always be available?

## Introduction
Effective inventory management is a complex task. Its complexity is due to the simultaneous impact of multiple factors. Some factors make the inventory management process quite difficult:
* We operate a wide assortment
* Items have different strategic importance
* Items have poor predictability, high variation
* Items have expiration dates, morally become obsolete
* Individual items have special storage conditions (freezers, aggressive)
* We use several/many suppliers
* The range of suppliers overlaps, but not completely
* Suppliers offer different terms of delivery, payment, prices
* Suppliers offer various discounts for larger quantities
* Suppliers deliver the items with defects, delays
* We have a relatively small warehouse
* Delivery is intended for several of our stores
* We accept reservations with a remote execution date
* Differences in working days/holidays between us and suppliers
* Others

Below we will begin by reviewing the simplified models - one item, one supplier, stable consumption, fixed quantity in one batch, etc. We will gradually add the variables to understand how specialists manage items in distribution centers with thousands of items and hundreds of suppliers.

## Key concepts

### Average inventory during the period
The task of estimating average stocks seems trivial at first glance. The most accurate indicators of average stocks could be given by a system that tracks current stocks in real time. But even it does not always give accurate values ​​when we need to plan the average stocks in the future. For planning purposes, we may use different to find average inventory, depending on the data available and the desired accuracy:

*a) Average inventory = Inventory level at the end of the current period*

$$ \overline{I}=Q_{end} $$

This approach is applicable to a very rough estimate. It gives relatively accurate values ​​if the products required for consumption in the current month are withdrawn from the warehouse at the very beginning of the period.

*b) Average inventory = Inventory level at the end of the current period + half of the SKU consumption for the period*

$$ \overline{I}=Q_{end}+\frac{D}{2} $$

The higher accuracy variation of the above model. Consider that products intended for consumption in the current month use a significant amount of warehouse capacity and have an impact on current and average stocks. It gives high accuracy when the products intended for consumption in the current month are consumed evenly throughout the period.
*c) Average inventory = (maximum inventory level + minimum inventory level) / 2*

$$ \overline{I}=\frac{Q_{\max}+Q_{\min}}{2} $$

*d) Average stock = the averaged stock data from several blocks (inventories)*

$$  \overline{I}= \sum \frac{Q_i}{n} $$

It is used when there is data collected about the availability in the warehouse during relatively short intervals of time. It gives the more accurate result the higher the frequency of +- checks and the more stable the stock level (low variability in consumption).

### Reorder Point - Reorder Point (R or ROP)
R - signal level for re-request. This is the level (eg number of items) below which the stock should not fall without the attention of the supply specialist. Upon reaching this level, the specialist usually orders a new batch of the item. R is calculated so that the stock in the warehouse is just enough for the time required for delivery. This way, the item is always in stock, the new lot arrives close to when the old one runs out.

### Safety Stock Level
Level of inventory in the warehouse necessary to avoid short-term shortages caused by fluctuations in demand, delivery delays, etc. Maintaining a warranty stock is associated with additional financial costs, "frozen money". Companies independently decide on the volume of warranty stock, in view of the level of service they aim to provide to their customers.

### Service level objective (SLO)
SLO is a percentage indicator reflecting the probability of the item being in stock.
For example, in wholesale and retail, a 95% SLO (or 95% service level) means that 95% of the time the customer will be able to purchase the item. Respectively, in 5% of cases, there will be a refusal to purchase the item due to the lack of available units.

### Service level agreement (SLA)
An agreement between the supplier and the customer to offer the item on negotiated terms at a target service level. For example, Supplier A guarantees that material shortages in its warehouse will not exceed 5% of the time. Such agreements are often concluded for strategically important materials.

## Stock dynamics
In today's market conditions, every company strives to optimize inventory management in order to operate with minimal amounts of working capital, minimal inventory holding costs, and minimal investment costs for building warehouse capacity. Characteristic features of an inventory management policy - the so-called "Inventory dynamics" for each item during a certain period.

### Basic formulas
Minimum level of stock in the warehouse:

$$ Q_{min}=SS $$

Maximum level of SKU in the warehouse:

$$ Q_{max}=Q_{min}+Q_{ord} $$

Average level of SKU in the warehouse:

$$ \bar{I}=\frac{Q_{max}+Q_{min}}{2} $$

Reorder point level: 

$$ R=\bar{d}L+SS $$

where:
\bar{d} - average daily consumption
L - time of execution of a delivery order after a request
Q_{max} - the maximum planned level of the item
Q_{min} - the minimum planned level of the item
\bar{I} - the item's average planned level
SS - amount of safety stock
Q_{ord} - the agreed quantity in one delivery
R - the critical stock level for reordering

### Repurchase Tier (R) Decisions
Specialists in the procurement or supply department monitor inventory levels. They should place orders for delivery of a new lot of the item before stocks approach critical levels. This is a tricky task as the items have different dynamics. For these needs, information systems are often equipped with a tool that signals the approach of the stock levels of a certain item to the critical level.
In the figure below, the ROP level signals the procurement department in need of requisitioning the new lot.

![](WARN_REPLACE_IMG_URL)
*Fig. 1. Point for the new purchase*

Dynamics of the stock of 1 item in one company:
-	Initial stock of the item - 40 pcs.
-	Average daily consumption - 5 pcs/day
- 	Quantity of 1 contractual delivery – 30 pcs.
-	Delivery time after request - 3 days (calendar)

**If the company operates without the warranty stock.**
We plan to deliver when

$$ Q_i = 0 $$

$$ R = 5 * 3 + 0 = 15 + 0 = 15 pcs $$

$$ Q_{max} = 0 + 30 = 30 pcs $$

$$ Q_{min} = 0 pcs $$

$$ \bar{I} = \frac{30+0}{2} = 15 pcs $$

![](images\dynamics-noSS-4weeks.png)
*Fig. 2. Dynamics of stocks without warranty stock*

**If the company provides for the warranty stock.**
Warranty, insurance stock - 10 pcs
If we plan SS to always be available, then the supply from Qword must be realized at the moment when the 10 pieces from the guarantee stock will be reached.

$$ R = 5 * 3 + 10 = 25 pcs $$

$$ Q_{max} = 10 + 30 = 40 pcs $$

$$ Q_min = 10 pcs $$

$$ \bar{I} = \frac{40+10}{2} = 25 pcs $$

![](images\dynamics-withSS-4weeks.png
*Fig. 3. Dynamics of stocks with warranty stock (vertical axis = stock level; horizontal axis = days)*

#### Reordering Point in distribution centers:
The point R for the entire distribution network is calculated in a similar way, substituting the values ​​for average values ​​for the entire chain:

$$ R=\bar{d}\cdot L+z\cdot\sigma_d\cdot\sqrt{L} $$

where:
L - time for delivery of the goods through the entire distribution chain: from the manufacturer, through DC, warehouses to retail auction.
\bar{d} – average daily consumption across all retailers
\sigma_d – standard deviation of aggregated demand from all retailers in the supply chain system
z = z(x) - service factor (from Table 1.)

**Table 1. Service factor according to the target service level**
| x | 90% | 92% | 95% | 97% | 99% | 99.9% | 
| --- | --- | --- | --- | --- | --- | --- |
| z | 1.29 | 1.46 | 1.65 | 1.88 | 2.33 | 3.08 | 

For example, if the target service level is 95%, the company should enter a service factor of 1.65 into the formula
You can independently calculate service factor using spreadsheets using function NORM.S.INV (or NORMSINV depending on software version)

### Decisions on the level of warranty stock
A safety stock has several purposes: to cover variations in consumption

#### The warranty stock to cover a set period
When we are given the target level of the guarantee stock in days, it means that we have to ensure such quantity in the stock that would be enough for the specified period:

$$ SS=\bar{d}\cdot T_{SS} $$

T_{SS} – consumption in days covered by the guarantee stock
**Example:**
Warranty, insurance stock = 2 days; Average daily consumption = 5 pcs/day

$$ SS = 5 * 2 = 10 pcs $$

#### The warranty stock to cover delivery time under force majeure conditions
Often, companies operate with the minimum permissible levels of insurance guarantee stock:

$$ SS=\bar{d}\cdot T_{urgent} $$

T_{urgent} – delivery time in case of force majeure (urgent delivery)

**Example:**
Express delivery time = 2 days; Average daily consumption = 5 pcs/day

$$ SS = 5 * 2 = 10 pcs $$

To achieve a higher level of service, the warranty stock can be increased.

#### The warranty stock to cover the target level of service
When consumption is volatile (eg items from Y or Z group), the practice is to increase the safety stock level in view of the variation in consumption and target service level.

$$ SS=z\cdot\sigma_d\cdot\sqrt{L} $$

sigma_d - the standard deviation of daily consumption,
z = z(x) - coefficient depending on the target (set, planned) level of service (*x*) to the customers. It is selected from a table. (Table 1)

#### High levels vs. low levels of warranty stock
Typically, high levels of warranty stocks apply to certain goods and business practices - pharmaceuticals from a warehouse serving a hospital, supply of sites of strategic importance.
According to David Simchi-Levi[^1] warranty stocks should not be maintained (except in the cases mentioned above), but efforts should be concentrated on defining*R*, so that there is never a shortage of stock with a probability higher than planned

### Request execution time

#### Fixed delivery time
Fixed delivery time is used in different situations:
a) procurement department does not care about high accuracy of estimates and bets an approximate number
b) the supplier has an absolutely strict production and delivery plan (JIT approach)
b) the deadline for production and incoming control can be ignored

#### Delivery time as sum of components
Request execution time (days):

$$ L=T_{prod}+T_{trans}+T_{in} $$

T_{prod} - time for making the order
T_{trans}  - time to transport the order
T_{in} - time for conducting incoming control

#### Consideration of uncertainty in the delivery time
When the procurement department observes variations in the actual delivery times, it is often the case that the request is sent several days earlier. Thus, delays on the supplier's side are expected to be reduced. This approach is acceptable when an earlier delivery causes fewer problems than a later one. To include this time buffer, the following formula applies:

$$ R = \bar d \cdot \bar L + z \cdot \sigma_L \cdot \bar d $$

When the variation has a strong impact on both demand and lead time, the following formula applies ([Source](https://slideplayer.com/slide/1480812/)):

$$ R=\bar{d} \cdot \bar{L}+z\cdot\sqrt{\bar{L} \cdot\sigma_d^2+\bar{d^2}\cdot\sigma_L^2} $$

#### Consideration of weekends/holidays
When planning deliveries, the procurement specialist takes into account the working days of both the own outlets and those of the supplier. Company holidays affect consumption, while supplier holidays affect delivery time. When calculating consumption time during the delivery time, holidays should be taken into account as follows:
* Only days that fall within the current delivery period are counted
* Company holidays are deducted from the delivery time
* Supplier holidays are added to the delivery time
* If the days off of the company and the supplier coincide

Assume that the company operates 6 days/week and the supplier 5 days/week.
Delivery is within 3 days. There is no warranty stock. We plan to deliver the moment when*Q**i* = 0
If we are approaching the holidays, then the request level will be:
*R* = 5 * (3 - 1 holiday (company) + 2 holidays (supplier)) + 0 = 20 + 0 = 20 pcs
If, however, the situation occurs at the beginning of a week - the request will be made at the level of R = 15 pcs:
*R* = 5 * (3 - 0 holiday (company) + 0 holiday (supplier)) + 0 = 15 + 0 = 15 pcs
If delivery time is more than one week, we include all weekends/holidays which

### Consideration of other factors
There are many modifications to the repurchase point formulas. Such modifications allow the tool to behave adequately in the complexity of the environment for which it is intended (factors complicating inventory management we have discussed above). Information systems manufacturers often make it a proprietary tool to maintain competitive advantages. This does not allow to freely consider the formulas embedded in multiple information systems. But the basis of all of them is the same.

## Inventory Management System (IMS)
Inventory Management System - is an information system that helps the procurement department to track inventory, to react when product stocks approach critical levels. IMS works in tight integration with enterprise resource planning (ERP) systems, warehouse management systems (WMS), and often its functions are directly embedded in these modules.

![](WARN_REPLACE_IMG_URL)
*Fig. 4. Devices working in a single IMS system*
The task of IMS is to provide accurate information about stock in the warehouse. Algorithms for the automatic release of requests to suppliers to replenish stocks in the warehouse are integrated into the individual systems. Typically, systems signal employees through a system of purchasing priorities. For the specific example above, the information system could issue the following signals:
1. When the specified item's stock levels approach near 35-30 (also depends on the consumption rate) the item will receive a base priority for purchase (eg, be marked green). This will show the procurement specialist that he can now include this item when forming a request for other items to the same supplier.
2. After crossing the limit of 25 items, the system should increase the item's priority to a higher one (for example, color it yellow). This means that the employee should place an order as soon as possible.
3. After crossing the limit of 15 pieces, the system should increase the item's priority to very high. This means that the warehouse has already started to "eat" the warranty stock and there is a high risk of falling into deficit.
4. There may be additional priority levels. For example, when the levels drop to 10-5 pieces, the system assigns the highest priority to the item (for example, colors it black). This means that a shortage is inevitable and the procurement specialist must seek channels for urgent supply of the item to reduce the risk.
5. It can also have negative priorities (eg colored blue or purple). This means that there is excess stock or the item is scheduled for sale/liquidation and specialists should purchase additional quantities from it only in exceptional cases.

![](WARN_REPLACE_IMG_URL)
*Fig. 5. Example of prioritization of purchase orders - Replenishment monitor in SAP. Source: logiplus.de*

## Integration of the ROP toolkit into popular ERP systems
SAP Source: help.sap.com/docs/
In reorder point planning, procurement is triggered when the sum of plant stock and firmed receipts falls below the reorder point .
The following values are important for defining the reorder point:
* Safety stock
* Average consumption
* Replenishment lead time
The following values are important for defining the safety stock:
* Past consumption values (historical data) or future requirements
* Vendor/production delivery timelines
* Service level to be achieved
* Forecast error, that is, the deviation from the expected requirements

Oracle Business Suite [https://docs.oracle.com/](https://docs.oracle.com/cd/A60725_05/html/comnls/us/inv/roplan.htm)
Reorder point planning uses demand forecasts to decide when to order a new quantity to avoid dipping into safety stock. Reorder point planning suggests a new order for an item when the available quantity--on-hand quantity plus planned receipts--drops below the item's safety stock level plus forecast demand for the item during its replenishment lead time. The suggested order quantity is an economic order quantity that minimizes the total cost of ordering and carrying inventory. Oracle Inventory can automatically generate requisitions to inform your purchasing department that a replenishment order is required to supply your organization.
Order lead time is the total of the item's processing, preprocessing, and postprocessing lead times.
If the forecast is correct and the order arrives on time, the inventory level should be right at the safety stock level at the time of receipt. In cases where the desired safety stock level changes during the order lead time, Oracle Inventory uses the largest safety stock quantity during the lead time.

Microsoft NAV [https://learn.microsoft.com/en-us/dynamics-nav-app/](https://learn.microsoft.com/en-us/dynamics-nav-app/design-details-the-role-of-the-reorder-point)
The planning system will suggest a forward-scheduled supply order at the point when the projected inventory passes below the reorder point.
The reorder point reflects a certain inventory level. However, inventory levels can move significantly during the time bucket and, therefore, the planning system must constantly monitor the projected available inventory.

## More information
[https://slideplayer.com/slide/1480812/](https://slideplayer.com/slide/1480812/) - Lesson 17 Inventory management
[https://www.inventoryops.com/safety_stock.htm](https://www.inventoryops.com/safety_stock.htm) - Optimizing Safety Stock. Terminology and calculations. Understanding the statistical model and factoring in additional variables.

[^1]: Designing and Managing the Supply Chain: Concepts, Strategies, and Case Studies, David Simchi-Levi, McGraw Hill Professional, 2003, ISBN: 9780072492569
