**Planview to Power BI: Automated MBR Reporting Dashboard**
***📊 Project Overview***
This project automates the data extraction and visualization process for Monthly Business Reviews (MBR). By replacing a manual, error-prone Excel workflow with a live API connection between Planview (Enterprise Project Management tool) and Power BI, I reduced monthly reporting prep time by 100% (saving 2–3 hours per month) and eliminated manual entry risks.

***🔴 The Problem***
The Strategic Initiatives team managed projects in Planview, but the platform lacked robust reporting capabilities. To prepare for the Monthly Business Review:

- Managers had to manually click every project card to find the latest status update.
- Data was copied and pasted into Excel, risking significant manual entry errors.
- The process was labor-intensive, requiring 2–3 hours of manual work every month.

***🛠️ The Solution (The Technical Process)***
Since native reporting was limited, I took the initiative to coordinate with Planview representatives to identify API capabilities.

1. Data Integration & Architecture
- API Connectivity: Established a secure connection using API tokens to pull live initiative data.
- Web Scraping/URL Connection: Discovered and integrated a specific "Comment Export" URL to bypass API limitations regarding project comments.
- Data Modeling: Designed a Star Schema to optimize performance.
- Fact Table: All initiative details and metrics.
- Dimension Tables: Project Metadata (Initiative Name, Point of Contact (POC), Timeline, Health Status).

2. Transformation & DAX Logic
- Dynamic Filtering: Developed DAX measures to filter and display only the most recent comment per Project ID, ensuring the MBR always showed the latest update.
- Conditional Formatting: Implemented RAG (Red, Amber, Green) status tracking for visual progress monitoring.

3. Automation & Delivery
- Scheduled Refresh: Configured an automated gateway refresh at 5:00 AM daily.
- PowerPoint Integration: Linked the Power BI live view directly into the MBR slide deck, allowing leadership to view real-time data without leaving their presentation environment.

***🚀 Impact & Results***
- Time Savings: Reduced manual data collection time from 3 hours to 0 minutes.
- Data Integrity: Eliminated human error from the "copy-paste" reporting method.
- Executive Visibility: The dashboard is now the primary tool used by leadership for monthly strategic decision-making.

***📸 Dashboard Preview***
