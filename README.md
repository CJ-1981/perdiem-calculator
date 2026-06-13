# **German Foreign Daily Allowance Calculator**

An interactive, responsive single-page web utility that computes correct legal daily allowances (*Verpflegungsmehraufwand*) for international corporate trips based on the latest German tax guidelines.

**Live demo:** [cj-1981.github.io/perdiem-calculator](https://cj-1981.github.io/perdiem-calculator/)

---

## **Screenshots**

### Trip Planner (Desktop)

The main workspace where you build your itinerary using a visual node-based timeline. Each stop shows a location selector (sorted alphabetically across 157 worldwide BMF locations), date/time picker, and optional meal deduction toggles. The right panel displays the total reimbursement claim in real time.

![Trip Planner Desktop](screenshot-trip-planner.png)

### BMF Rate Database

Browse, search, add, and delete BMF per-diem rates. The table loads dynamically from `bmf-rates.json` and supports CSV/JSON file import for custom rate tables. Rates are always fetched fresh on page load, with user overrides persisted separately in localStorage.

![BMF Database](screenshot-bmf-database.png)

### Mobile Responsive

The interface adapts to narrow viewports with touch-friendly controls, scrollable panels, and no horizontal overflow.

![Mobile View](screenshot-mobile.png)

---

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

### **4\. BMF Directory CSV/JSON Integration**

Supports importing custom external BMF tables via CSV or JSON, matching:

```
Location, FullRate, SmallRate, Currency
```

Files can be uploaded via the file picker or drag-and-dropped onto the page.

### **5\. Dynamic Rate Loading**

BMF rates are loaded from an external `bmf-rates.json` file at runtime, covering **157 worldwide locations**. This enables independent rate updates without touching application code.

* **Online:** Always fetches the latest `bmf-rates.json` and merges with any user-defined custom overrides.
* **Offline:** Falls back to cached rates (with a toast notification), or to a minimal emergency fallback if no cache exists.
* **Custom overrides** are persisted separately from the base rates, ensuring they survive both offline sessions and future base rate updates.

### **6\. Print-Ready Expense Statement**

One-click print layout generates a formatted expense statement with daily breakdowns, totals, and audit signature lines — optimized for paper or PDF output.

---

## **Tech Stack**

* React 18 (CDN)
* Tailwind CSS (Play CDN)
* Babel (in-browser JSX compilation)
* Zero build step — single `index.html` deployment