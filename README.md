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

---

#  Database Schema (PostgreSQL)

## **tenants**
| column | type | description |
|-------|------|-------------|
| id | SERIAL PK | tenant id |
| store_name | text | Name of Shopify store |
| shopify_store_domain | text | my-store.myshopify.com |
| shopify_access_token | text | Private access token |
| created_at | timestamp | Registered time |

## **customers**
| column | type |
|--------|-------|
| id | SERIAL PK |
| tenant_id | FK → tenants |
| shopify_customer_id | bigint |
| email | text |
| first_name | text |
| last_name | text |
| total_spent | numeric |
| updated_at | timestamp |

## **products**
| column | type |
|--------|-------|
| id | SERIAL PK |
| tenant_id | FK |
| shopify_product_id | bigint |
| title | text |
| price | numeric |
| created_at | timestamp |

## **orders**
| column | type |
|--------|-------|
| id | SERIAL PK |
| tenant_id | FK |
| shopify_order_id | bigint |
| customer_id | bigint |
| total_price | numeric |
| created_at | timestamp |

## **events**
| column | type |
|--------|-------|
| id | SERIAL PK |
| tenant_id | FK |
| type | text |
| data | jsonb |
| created_at | timestamp |

---

#  API Documentation

### **Tenant Onboarding**
```http
POST /api/tenants/register
POST /api/tenants/login
POST /api/tenants/connect-shopify

Ingestion Endpoints
POST /api/ingest/customers?tenant_id=
POST /api/ingest/orders?tenant_id=
POST /api/ingest/products?tenant_id=
POST /api/ingest/events?tenant_id=

Analytics
GET /api/analytics/summary?tenant_id=
GET /api/analytics/orders-by-date?tenant_id=&start=&end=
GET /api/analytics/top-customers?tenant_id=


