# 📦 Prescriptive Inventory Engine (Chakan Node Deployment)

An enterprise-grade prescriptive supply chain optimization system engineered using live, anonymized transactional logs from an operational storefront in the heavy industrial hub of **Chakan (Pune, India)**.

## 🚀 The Core Problem Solved
The physical storefront was trapped in an operational gridlock: a paralyzing **40% stockout index on high-velocity cash drivers** occurring simultaneously with a massive **working capital freeze across a tail of over 3,000 product lines**. Reorder liquidity was completely locked up in stagnant, low-margin inventory on shelves. 

This engine replaces gut-instinct procurement with data-driven guardrails—**systematically locating the dead weight, unfreezing capital, and automating procurement loops.**

---

## 🔬 Core Engineering Milestones

*   **The Gross Margin Ghost Fix:** Uncovered and repaired a system logging glitch where missing `COST RATE` entries defaulted to `0`, creating a false 100% margin on half the catalog. Deployed a **Brand-Proximity Proportional Imputation Routine** to reverse-engineer true brand cost structures.
*   **The Zero-Bypass Filter:** Built a custom conditioning filter that isolates zero-sale rows. This prevented the mathematical quartiles from collapsing to zero, enabling accurate segmentation of actual consumer demand velocity.
*   **Dynamic Order Guardrails:** Automated restocking thresholds (`Suggested_Min_Stock` and `Suggested_Max_Stock`) on a rolling basis. The algorithm establishes safety floors based on historical minimums and applies a **defensive 10% reduction cap strictly to low-risk, flat-demand Evergreen items** to prevent cash from being frozen again.

---

## 👑 Major Empirical Findings

By crossing a **Pareto 80/20 Filter** with an **ABC Velocity Index** and an **XYZ Demand Volatility Model** (Coefficient of Variation, $\sigma/\mu$), the engine revealed an intense wealth concentration across the catalog:

*   **The 80/20 Reality:** The top 20% of unique items generate **99.89% of total storefront revenue ($526.4M out of $527.0M total sales)**.
*   **Grid 2 (High Vol | High Profit | Stable):** Represents **29.05%** of store revenue. This is the store's primary bedrock engine. 
*   **Grid 8 (Slow Vol | Low Profit | Stable):** Represents **0.00%** of total revenue. These lines are absolute dead capital traps. 

---

## 🛠️ Operational Directives
1.  **Liquidate Grid 8 & Dormants:** Immediately freeze procurement and run markdown campaigns to convert non-moving dead weight back to liquid cash.
2.  **Fund Grid 2 & 4 Core Drivers:** Channel newly freed liquidity into restocking high-velocity, high-demand items to plug the 40% stockout leak.
3.  **Acknowledge Temporal Constraints:** Because the data spans a 90-day window (*May, June, July*), volatility metrics capture short-term demand variance. In production, this engine operates as a rolling short-term operational control script that moves forward dynamically month-over-month.

---

## 📂 Installation
```bash
git clone https://github.com
pip install -r requirements.txt
python src/engine_pipeline.py
```

*Data Note: All personally identifiable information (PII) and corporate identifiers have been strictly masked or scaled to protect enterprise anonymity while maintaining absolute operational distribution authenticity.*
