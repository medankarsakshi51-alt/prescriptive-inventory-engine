# Prescriptive Inventory Engine (Chakan Store Deployment)

This is a real-world supply chain optimization project built using active, anonymized transactional data from a physical retail store running in the heavy manufacturing and industrial hub of **Chakan (Pune, India)**. 

---

## 🛑  The Problem: A Store Suffocating in its Own Inventory

Imagine running a busy retail store with plenty of daily customer traffic. On paper, business looks good, but behind the scenes, you are facing a nightmare: **40% of the time a customer asks for a top-selling product, it's out of stock.** Frustrated customers are leaving empty-handed and going straight to competitors.

When you try to re-order those popular products, you find out the store's bank account is bone dry. The money hasn't vanished—it is completely trapped. Thousands of dollars are frozen on dusty shelves in the form of slow-moving, low-margin "dead stock" that nobody wants to buy. 

Because the business was being run on gut instinct rather than real data, it was trapped in a vicious cycle: ordering the wrong items, freezing its cash flow, and triggering massive stockouts on the products that actually keep the lights on.

---

##  The Solution: Unfreezing Capital via Mathematical Guardrails

To fix this, we built a prescriptive automation engine that steps in and acts as a data-driven assistant for the store owner. 

First, we isolated the **Dormant Stock** (items that didn't sell a single unit in three months) and **Grid 8 Items** (slow-moving products with terrible profit margins). The directive here is clear: stop ordering them immediately and run markdown sales to liquidate them back into cold, hard cash.

Next, we mapped out where to reinvest that newly freed cash. The math pointed directly to **Grid 2**—our "Evergreen Winners." These are high-volume, high-profit products with extremely flat, predictable demand. We also prioritized funding for **Grid 3 and 4** products. They have lower profit margins, but because they are daily high-velocity staples, they are the primary drivers of store foot traffic. Keeping them stocked plugs the 40% stockout leak.

Finally, we automated the procurement process. The engine calculates an optimized **Minimum Safety Floor** (based on historical lowest sales months) so shelves are never empty. It also sets an automated **Maximum Stock Cap**. If a product's demand is wild and erratic, the cap expands to capture peak sales. But if a product's demand is perfectly flat and predictable, the system applies a **defensive 10% reduction cap** to strip away unnecessary padding. This ensures the store stays incredibly lean and never freezes its working capital again.

---

## The Challenges: Overcoming the Traps in the Raw Data

Building this engine wasn't straightforward. The raw data coming from the store's physical point-of-sale system was full of structural anomalies that would have completely ruined a standard analysis. 

*   **The 100% Profit Margin Illusion:** When we first looked at the catalog, over 50% of the products showed a perfect profit margin of 100%. This was a massive system error. Whenever the cashier or manager logged a product without inputting its wholesale cost, the database defaulted the cost to `0`. This made hundreds of products look entirely free to acquire. Deleting these rows would have ruined the dataset. Instead, we wrote an algorithm that grouped items by their brand name strings, calculated the true historical cost ratios of the valid items in that brand family, and proportionally mapped those real costs onto the missing rows.

*   **The Zero-Sales Velocity Collapse:** Because this is a massive catalog of over 3,000 items, a huge chunk of products registered exactly `0` sales in individual months. If you try to calculate standard statistical quartiles (breaking volume into low, medium, and high velocity buckets) with those zeros left in the mix, the math collapses. The midpoint drops straight to zero, making it impossible to separate a slow-moving staple from an item that has truly died. We built a custom conditioning filter that temporarily strips zero rows, calculates pure velocity quartiles against active inventory, and safely routes zero-transaction lines into their own category.
   
*   **The 90-Day Timeline Limit:** The data spans a specific three-month window (*May, June, July*). Because of this short timeline, our volatility metrics capture short-term demand variance rather than annual macro-seasonality. An item flagged as highly volatile might just be undergoing a standard summer demand shift, while a flat line might see a huge festive spike in Q4 (like Diwali). We had to explicitly note this constraint: in a live production environment, this engine must run as a rolling script that continually updates month-over-month to keep purchasing safely aligned with shifting seasonal trends.

---

## 📂 Installation & Execution
```bash
git clone https://github.com
pip install -r requirements.txt
python src/engine_pipeline.py
```

*Data Privacy Note: All personally identifiable information (PII), specific pricing, and corporate identifiers have been strictly masked or scaled to respect corporate anonymity while maintaining absolute operational distribution authenticity.*

