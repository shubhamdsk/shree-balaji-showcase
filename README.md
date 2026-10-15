<div align="center">
<img src="https://shree-balaji.shreebalajipaints.workers.dev/images/brand/logo-v2.webp" alt="Shree Balaji Logo" width="120" />
<h1>🎨 Shree Balaji Paints, Plywood & Hardware</h1>
<p><strong>A phone-first digital product catalogue, quotation builder, paint calculator, and store management platform built for an authorised Asian Paints dealer in Kotul.</strong></p>

<p>
<a href="https://shree-balaji.shreebalajipaints.workers.dev/" target="_blank" rel="noopener noreferrer">
<img src="https://img.shields.io/badge/Live_Storefront-Visit_Site-2563eb?style=for-the-badge&logo=googlechrome&logoColor=white" alt="Live Site" />
</a>
<a href="https://software-studio.nexoralab.workers.dev/" target="_blank" rel="noopener noreferrer">
<img src="https://img.shields.io/badge/Built_By-Nexora_Studio-0f172a?style=for-the-badge" alt="Nexora Studio" />
</a>
<img src="https://img.shields.io/badge/Status-Production_(Delivered)-16a34a?style=for-the-badge" alt="Delivered" />
</p>

<p>
<img src="https://img.shields.io/badge/Next.js-000000?style=flat-square&logo=nextdotjs&logoColor=white" alt="Next.js" />
<img src="https://img.shields.io/badge/React-20232A?style=flat-square&logo=react&logoColor=61DAFB" alt="React" />
<img src="https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white" alt="TypeScript" />
<img src="https://img.shields.io/badge/Tailwind_CSS-38B2AC?style=flat-square&logo=tailwind-css&logoColor=white" alt="Tailwind CSS" />
<img src="https://img.shields.io/badge/PostgreSQL_(Neon)-4169E1?style=flat-square&logo=postgresql&logoColor=white" alt="PostgreSQL" />
<img src="https://img.shields.io/badge/Drizzle_ORM-C5F74F?style=flat-square&logo=drizzle&logoColor=black" alt="Drizzle ORM" />
<img src="https://img.shields.io/badge/Cloudflare_Workers-F38020?style=for-the-badge&style=flat-square&logo=cloudflare&logoColor=white" alt="Cloudflare Workers" />
</p>
</div>

---

> **🔒 Intellectual Property Notice:** This repository serves as a **public case study & architecture showcase**. Because this is a commercial production system built for a live retail client by **<a href="https://software-studio.nexoralab.workers.dev/" target="_blank" rel="noopener noreferrer">Nexora Studio</a>**, the proprietary source code is maintained in a private repository.

---

## 📸 Storefront Overview

Designed for homeowners, painters, and contractors in Kotul, blending trustworthy local Marathi messaging (*"घर सजवण्यासाठी लागणारं सगळं — एकाच ठिकाणी"*) with a fast, modern product discovery experience.

<div align="center">
<img width="100%" alt="Shree Balaji Paints Storefront Preview" src="https://software-studio.nexoralab.workers.dev/api/media/de71d2a3-9556-4477-8878-d3d15dbb78d1.jpg" />
</div>

---

## 🛍️ Live Product Catalogue & Visual Media Pipeline

Instead of static hard-coded assets, product categories and inventory items are dynamically served from **Neon Serverless PostgreSQL** via **Drizzle ORM** and optimized through Next.js edge media routes.

|                                                               🎨 Authorised Paints (26+ Products)                                                              |                                                                             🧱 Paint Preparation (21+ Products)                                                                            |                                                                            🖌️ Painting Tools (18+ Products)                                                                            |
| :------------------------------------------------------------------------------------------------------------------------------------------------------------: | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: |
| <img width="300" alt="Paints" src="https://shree-balaji.shreebalajipaints.workers.dev/images/categories/paints-packs.jpg" /> | <img width="300" alt="Paint Preparation" src="https://shree-balaji.shreebalajipaints.workers.dev/api/photos/1f523006-c451-458b-8195-ddeb74ffbfbd.jpg" /> | <img width="300" alt="Painting Tools" src="https://shree-balaji.shreebalajipaints.workers.dev/api/photos/6dcd3674-8247-458e-94d9-960164ef1150.jpg" /> |

|                                                                              🪵 Plywood & Boards (12+ Products)                                                                             |                                                              ✨ Decorative Laminates (16+ Products)                                                             |                                                                              🚪 Doors & Hardware (11+ Products)                                                                             |
| :-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: | :------------------------------------------------------------------------------------------------------------------------------------------------------------: | :-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: |
| <img width="300" alt="Plywood and Boards" src="https://shree-balaji.shreebalajipaints.workers.dev/api/photos/6561b37b-98da-42b1-b4f7-292d6d0417a0.jpg" /> | <img width="300" alt="Laminates" src="https://shree-balaji.shreebalajipaints.workers.dev/images/categories/laminates.jpg" /> | <img width="300" alt="Doors and Fittings" src="https://shree-balaji.shreebalajipaints.workers.dev/api/photos/075d0e17-5f81-42d8-aee0-9e387c27090c.jpg" /> |

---

## 🚀 Key Product Features Engineered

### 1. 📋 Interactive Quotation Builder & WhatsApp Enquiry Flow
In local hardware, plywood, and paint retail, rates fluctuate daily and customers prefer confirming bulk rates on WhatsApp rather than using standard e-commerce checkouts.
- Customers browse categories and add paints, primers, plywood sheets, and fittings to a custom **Quotation List** (`/quotation`).
- One-tap export formats the entire itemised list into a structured **WhatsApp enquiry** sent directly to the shop owner (`+91 7038499108`).

### 2. 🧮 Built-In Paint Coverage Calculator
Homeowners rarely know how many litres of primer, putty, or emulsion are required for their walls. The built-in calculator estimates material quantities based on dimensions before the customer sends an enquiry.

### 3. 🔐 Self-Service Owner Admin Panel
Gives the store owner full autonomy to:
- Add, edit, and toggle stock status for products across 7+ categories.
- Upload and manage product photography dynamically.
- Publish seasonal and festive discounts on the **Offers** page (`/offers`) without developer intervention.

---

## 🏗️ System Architecture

```mermaid
flowchart LR
    A[Customer Mobile Browser] -->|Edge SSR & Asset Caching| B[Cloudflare Workers - Next.js]
    C[Store Owner Admin Panel] -->|Authenticated CRUD| B
    B -->|Type-Safe SQL Queries| D[Drizzle ORM]
    D -->|Serverless Pool| E[(Neon PostgreSQL DB)]
    B -->|Optimized Edge Image Caching| F[Next.js Image Pipeline]
    A -->|Formatted Quotation List| G[WhatsApp Business API]
```
## ⚡ Technical Highlights

* **Edge-First Deployment:** Hosted on **Cloudflare Workers** for near-zero cold starts and fast page loads on mobile connections.
* **Type-Safe Data Layer:** Powered by **Neon Serverless PostgreSQL** and **Drizzle ORM** for minimal bundle overhead on edge runtimes.
* **Bilingual & Accessible UX:** Semantic HTML5 landmarks, screen-reader support, and native `lang="mr"` Devanagari typography alongside English navigation.

---

## 📬 Architected & Delivered By

**Shubham Deshmukh** — Founder & Lead Developer at **<a href="https://software-studio.nexoralab.workers.dev/" target="_blank" rel="noopener noreferrer">Nexora Studio</a>**

* 🌐 **Studio Website:** <a href="https://software-studio.nexoralab.workers.dev/" target="_blank" rel="noopener noreferrer">software-studio.nexoralab.workers.dev</a>
* 💼 **LinkedIn:** <a href="https://www.linkedin.com/in/shubham-deshmukh1720" target="_blank" rel="noopener noreferrer">linkedin.com/in/shubham-deshmukh1720</a>
* 💻 **GitHub:** <a href="https://github.com/shubhamdsk" target="_blank" rel="noopener noreferrer">@shubhamdsk</a>
