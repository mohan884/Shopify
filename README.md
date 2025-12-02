# Shopify Multi-Tenant Data Ingestion & Insights Platform  
### uilt with Node.js, Next.js & PostgreSQL | Deployed on Vercel

A complete multi-tenant Shopify data ingestion and analytics system designed for enterprise retail use-cases.  
This project was built as part of the Forward Deployed Engineer (FDE)  simulates how real retailers onboard their Shopify stores and analyze customer, order, and product data.

---

#  Features

##  Shopify Data Ingestion
- Fetches **Customers**, **Orders**, **Products**, and **Custom Events**
- Connects via Shopify Admin REST APIs
- Supports manual sync + scheduled sync (cron / webhook-ready)
- Handles API rate limits and pagination
- Ensures consistent mapping into PostgreSQL tables

##  Multi-Tenancy Support
- Each Shopify store onboarded becomes a **tenant**
- Every record in DB is linked to a **tenant_id**
- Separate data spaces for each merchant
- Tenant-level auth and access control

##  Insights Dashboard (Next.js)
- Total revenue, orders & customers
- Orders by date (with filters)
- Top 5 customers by spend
- Real-time charts using Recharts
- Mobile-friendly UI with reusable components

##  Tenant Onboarding & Auth
- Email-based authentication
- Secure API key handling
- Tenant creation flow
- Connect Shopify store through Admin API credentials

---

#  Tech Stack

### **Backend**
- Node.js  
- Express.js  
- PostgreSQL (SQL-based analytics)  
- pg / Prisma / Sequelize (based on implementation)

### **Frontend**
- Next.js  
- React  
- Recharts (charts)  


### **Deployment**
- **Vercel** (Backend + Frontend)  

---

# 🏗️ System Architecture

