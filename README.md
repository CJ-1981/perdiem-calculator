# **German Foreign Daily Allowance Calculator**

An interactive, responsive single-page web utility that computes correct legal daily allowances (*Verpflegungsmehraufwand*) for international corporate trips based on the latest German tax guidelines.

## **Key Features & Calculations**

### **1\. Border Crossing (Mitternachtsprinzip)**

Following modern German income tax regulations (§ 4 Abs. 5 Satz 1 Nr. 5 EStG), if a traveler crosses multiple borders, the allowance is decided by the destination reached *last* on that day before midnight (24:00).

* On return trips back home, the rate of the last active foreign location dictates the claim payout.

### **2\. Multi-Stop Node Topology Timeline**

You can dynamically build your itinerary by adding visual node markers representing your stops. Adding or rearranging dates triggers real-time visual line connection updates and generates correct individual daily rows.

### **3\. Meal Deductions**

Provided meals (e.g. at hotels, client events, or flights) must lead to legal reductions from the full 24h allowance rate of that respective location:

* **Breakfast:** \-20% of the full daily rate.  
* **Lunch:** \-40% of the full daily rate.  
* **Dinner:** \-40% of the full daily rate.  
* *Calculation safeguard:* Payout cannot fall below €0 for any given day.

### **4\. BMF Directory CSV Integration**

Supports importing custom external BMF tables via CSV or JSON, matching:

Location, FullRate, SmallRate, Currency