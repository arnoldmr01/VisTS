# VisTS – Multi-Perspective Visualization of Global Aid Flows

This project explores the **AidData donor–recipient dataset (1947–2013)** using three complementary web-based visualizations.  
Across all views we focus on:

- **Top 20 donors** (countries and multilateral institutions)
- **Top 10 recipients**
- **Top 5 aid purposes** (for the purpose-based view)

Together, the three pages help answer:

- Who are the major donors and recipients?
- How much do they give or receive, and with whom?
- What purposes does the money support?
- How do these relationships change over time?


## How to run

1. Use python to open a server`python -m http.server 8001` or `python3 -m http.server 8001` depends on your python version

2. Make sure the CSVs (AidDataCoreDonorRecipientYearPurpose_ResearchRelease_Level1_v3.1.csv) is in the same directory with `index.html`, `index_1.html`, `index_2.html`, `index_3.html`

3. You can use the button on the top to switch the charts from `index_1.html` to `index_3.html`

3. Open the URL http://localhost:8001/index.html




## Visualization 1 – Aid Flow Overview (`index_1.html`)

**Goal:**  
Give a **high-level overview of who donates to whom and how much** among the main actors in the global aid system.

**Design:**  

- **Sankey diagram**
  - **Left nodes:** top 20 donors (countries + multilateral institutions)
  - **Right nodes:** top 10 recipients
  - **Links:** flows from donor → recipient  
    - Link **thickness** encodes total commitment amount.
- **Color encoding**
  - Donors use a cool gradient; recipients use a warm gradient.
  - Darker nodes = larger total amounts within that group.
- **Inline labels**
  - Each node label includes its **total aid amount**, so users can compare overall scale without extra charts.

**How to read / interact:**

- Scan the **left side** to identify **major donors** (largest totals and thickest outgoing links).
- Scan the **right side** to find **major recipients**.
- Follow individual links to see which donor–recipient pairs dominate global aid.
- Hover / click (if enabled) to see detailed information in the insight panel (exact amounts and ranked partners).


## Visualization 2 – Purpose-Based Decomposition (`index_2.html`)

**Goal:**  
Show **what the money is used for** by breaking aid flows into the **top 5 purpose categories** for each donor–recipient pair.  
Questions it supports:

- Do donors support a recipient across many sectors or concentrate on one?
- Are certain purposes (e.g., infrastructure, social services) systematically favored?

**Design:**

- **Matrix layout**
  - **Rows:** top 20 donors  
  - **Columns:** top 10 recipients  
  - Each cell = one **donor–recipient pair**.
- **Embedded pie charts**
  - Each cell contains a pie chart showing the **proportion** of the top 5 purposes for that pair.
  - Consistent colors are used for each purpose across the whole matrix.
- **Cell background shading**
  - Cell **background light→dark blue** encodes the **total amount** associated with that pair (darker = more money).

**How to read / interact:**

- Look across a **row** to see how a donor’s aid purposes differ between recipients.
- Look down a **column** to see how a recipient’s inflows are distributed by purpose across donors.
- Hover over a cell to see a tooltip with:
  - Total amount represented by the top 5 purposes
  - A ranked breakdown of each purpose in both **dollar value and percentage share**.


## Visualization 3 – Temporal Dynamics (`index_3.html`)

**Goal:**  
Reveal **how aid relationships change over time**: which partnerships grow, decline, or remain stable.  
Questions it supports:

- How does a donor’s total aid change year by year?
- For a given donor, which recipients become more important over time?
- Are there sudden shifts in allocation patterns?

**Design:**

- **Stacked area chart**
  - X-axis = **year**
  - Y-axis = **total annual commitments for a selected donor**
  - Each colored band = one of the **top 10 recipients** for that donor.
  - The **vertical thickness** of a band at a given year shows the amount that recipient received in that year.
  - The **overall stack height** shows the donor’s total aid volume that year.
- **Interactive legend & focus**
  - Legend entries correspond to recipients and can be hovered or toggled to focus on specific countries.
- **Tooltips**
  - Hovering over a point shows the **exact amount** given to the selected recipient in that year.

**How to read / interact:**

1. Choose a donor (via controls / dropdown, depending on implementation).
2. Observe:
   - Long-term growth or decline in the donor’s **total aid**.
   - Changes in the **relative thickness** of recipient bands (who becomes more or less important).
3. Hover over a band to:
   - See precise year-by-year values.
   - Temporarily fade other bands to highlight one recipient’s trajectory.

