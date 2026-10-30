Smart India Hackathon Workshop
Problem Statement Submission: SIH 26033
Date: 23/10/26
Reference Number: 26000161
Name: Manoj N
Problem Title
SIH 26033: Multiple intermediaries reduce farmers’ earnings and increase consumer prices.
Problem Creator’s Organization
Ministry of Consumer Affairs, Food & Public Distribution
Theme
Agriculture, FoodTech & Rural Development
Problem Description
Multiple layers of intermediaries between the farm gate and the consumer capture a large share of the final price. Farmers receive a small fraction of what consumers pay, while retail prices remain high because of inefficient handling, fragmented logistics, and information asymmetry. The problem statement expects a digital marketplace that connects farmers and Farmer Producer Organizations (FPOs) directly with consumers and bulk buyers, provides logistics support, and uses AI for demand forecasting and route optimization.
Expected Solution
•	Connects farmers and FPOs directly with consumers and bulk buyers.
•	Provides logistics support.
•	Uses AI for demand forecasting and route optimization.
Expected Benefits
•	Better prices for farmers.
•	Lower prices for consumers.
•	Reduced supply chain inefficiencies.
Proposed Solution
Our proposed solution is “KisanSetu Forward”, a pre-harvest demand-commitment marketplace. Instead of farmers harvesting first and searching for buyers later, the platform matches demand to supply before the crop is sown or harvested. Consumers, retailers, canteens, and bulk buyers place forward orders on the platform. An AI model forecasts district-level demand and pools these orders with the expected output of nearby FPOs. Farmers and FPOs then receive a committed buyer, a price agreed in advance, and a pickup slot, which removes most of the middlemen who exist only to absorb market uncertainty.
1. Detailed Explanation of the Proposed Solution
•	Supply onboarding. Farmers and FPOs register with land, crop, and expected-yield details. The platform verifies identity through Aadhaar-based eKYC (with consent) and links FPO membership records.
•	Demand aggregation. Consumers, households, retailers, hotels, and institutional kitchens place recurring or forward orders for specific produce, grade, and delivery window. Bulk buyers can place tender-style orders.
•	Demand forecasting. An AI model combines historical mandi prices, weather data, festival calendars, and locality-level order history to forecast demand for each commodity and district. The forecast tells FPOs what to plant or stock and tells buyers when prices are likely to be stable.
•	Batching and price discovery. Orders from the same area and the same commodity are merged into batches. A batch is released to a farmer or FPO with a fixed price band linked to a published reference index, so the farmer knows the minimum price before harvest.
•	Logistics and return-leg routing. Pickups are collected from village collection points (hubs run by FPOs or trained local entrepreneurs, called “Sanchalaks”). Trucks that travel empty back from urban markets are assigned to these pickups, and the AI route optimizer plans multi-stop routes that minimize distance and spoilage.
•	Payments and traceability. Payments are held in an escrow account and released to the farmer or FPO within 24 hours of delivery confirmation via QR or geo-tagged proof. Digital receipts give consumers traceability back to the farm.
•	Farmer interface. Farmers see live prices, buyer demand, advisory alerts, and their earnings in Hindi, English, and regional languages through a low-bandwidth app and an IVR (voice call) channel for feature phones.
2. How It Addresses the Problem
Problem Cause	How KisanSetu Forward Addresses It
Farmers sell at harvest, when prices are lowest	Forward commitments and price bands fixed before harvest remove distress selling.
Each intermediary takes a margin for risk and information gaps	Direct demand visibility and escrow payments reduce the risk premium that middlemen charge.
Fragmented, empty return trips raise logistics cost	Return-leg routing and multi-stop optimization spread transport cost across many loads.
Spoilage from delays and poor handling	Pickup slots, hub-based collection, and shorter chains reduce time from farm to buyer.
Consumers cannot see where prices are inflated	Transparent price breakdown on every order shows farmer share, logistics, and platform fee.
Small farmers lack bargaining power and credit	FPO-level aggregation gives collective bargaining power; escrow payments speed up cash flow.
3. Innovation and Uniqueness of the Solution
•	Demand-first, not harvest-first. Most agri-marketplaces start from the harvest and look for buyers. KisanSetu Forward starts from demand and asks farmers to grow for it, which is a different model with a different risk profile.
•	Return-leg logistics sharing. Empty trucks returning from city markets carry farm inputs out and produce back. The solution makes this return capacity available for produce pickup, cutting logistics cost without adding new vehicles.
•	Supply-demand matching model. Locality-level demand signals are combined with each FPO’s crop plan and yield estimate, so the forecast is tied to what can actually be supplied.
•	Transparent pricing band. A published reference price band is calculated from mandi data and weighted by the batch’s grade and delivery window. Farmers can see how their price was set.
•	Local hub entrepreneurs. Village “Sanchalaks” act as local hub operators, creating rural livelihoods and reducing dependence on outside intermediaries.
•	Built for low connectivity. Works on basic smartphones and feature phones through offline-first design, SMS, and IVR.
Technical Approach
1. Technologies to Be Used
Layer	Technology	Purpose
Mobile app (farmers)	Flutter (Dart), offline-first with SQLite	Cross-platform app that works with intermittent connectivity
Web app (buyers, FPOs, admin)	React with Next.js, Tailwind CSS	Order placement, batch management, and dashboards
Voice channel	Exotel or Twilio IVR, Bhashini APIs for speech-to-text and translation	Feature-phone access in regional languages
Backend services	Node.js (NestJS) for core APIs; Python (FastAPI) for AI services	Business logic and ML model serving
Demand forecasting	Python, Prophet and LightGBM; features from AgMarkNet price data and IMD weather data	District-level demand and price forecasts
Route optimization	Google OR-Tools (vehicle routing with time windows), OpenStreetMap, OSRM	Multi-stop and return-leg route planning
Database	PostgreSQL with PostGIS; Redis for caching	Transactions, geospatial hub mapping, and fast lookups
Payments and escrow	Razorpay Route or UPI-based escrow APIs	Holding payments and releasing them after delivery
Identity	DigiLocker and Aadhaar eKYC (consent-based), OTP login	Verified farmer and FPO identity
Traceability	QR codes, geo-tagged photos, and a hash-chained audit log	Proof of pickup and delivery
Infrastructure	AWS or MeitY-empanelled cloud (Mumbai/Hyderabad region), Docker, Kubernetes	Scalable, data-sovereign hosting
Security	OAuth 2.0 / JWT, TLS 1.3, role-based access, data encryption at rest	Protection of personal and financial data
2. Methodology and Process for Implementation
The implementation follows four phases over roughly six months, with a working prototype delivered at the end of Phase 1 and a pilot in two districts at the end of Phase 3.
Phase	Duration	Key Activities	Deliverable
1. Prototype	Weeks 1–6	Requirement capture with 2 FPOs; core order-to-payment flow; basic price band logic	Working prototype (web and Android)
2. Intelligence	Weeks 7–12	Train demand forecasting model on historical mandi and order data; build batching engine; integrate route optimizer	Forecast accuracy report; route plans for test data
3. Pilot	Weeks 13–20	Pilot in two districts (one producing, one consuming); onboard 20 FPOs, 200 farmers, 10 bulk buyers; IVR launch	Pilot dashboard and impact metrics
4. Scale	Weeks 21–26	Security audit; load testing; hub-operator training; state-level rollout plan	Production release and rollout playbook
Process Flow
Demand order is placed → AI forecast checks feasibility → order is batched by locality and commodity → FPO or farmer accepts a fixed price band → pickup is scheduled on a return-leg truck → produce is collected at a village hub and weighed with geo-tagged proof → buyer confirms delivery → escrow releases payment to the farmer or FPO within 24 hours → farmer and buyer both receive a transaction record. Feedback from each completed batch retrains the forecast model every week.
[Insert flowchart image here: Order → Forecast → Batch → Accept → Collect → Deliver → Escrow Release]
Feasibility and Viability
1. Analysis of Feasibility
•	Technical feasibility: Mobile penetration in rural India has grown substantially, and existing government platforms such as e-NAM, eNAM-linked FPO schemes, and Agri Stack (farmer ID and land records) provide reusable digital public infrastructure.
•	Market feasibility: Pre-order and forward-contract models are already used in parts of the private food sector. The solution applies the same logic to smallholder FPOs with aggregation and escrow.
•	Financial viability: The platform earns a small transaction fee (for example, 1.5–2% on the order value) and a subscription fee for bulk buyers. At scale, return-leg logistics reduces transport cost per kilogram for all participants.
•	Policy alignment: The Farmer Producer Organization scheme and the Digital Agriculture Mission support the required institutional and digital infrastructure, making government partnership realistic.
2. Potential Challenges and Risks
Risk	Likelihood	Impact
Low digital literacy among farmers	High	High
Forecast errors leading to unsold or unfilled orders	Medium	High
Existing middlemen resisting the model	High	Medium
Poor connectivity in remote villages	High	Medium
Spoilage during transit for perishable produce	Medium	High
Data privacy and consent concerns	Low	High
Price volatility causing disputes over fixed bands	Medium	Medium
3. Strategies for Overcoming These Challenges
•	Digital literacy: Voice-based interface, local-language support, and trained Sanchalaks who assist farmers in person at hub locations.
•	Forecast errors: Start with a small set of high-demand commodities. Use conservative forecast bands and allow partial-batch fulfilment so one shortfall does not cancel a whole order.
•	Intermediary resistance: Partner with existing traders and FPO leaders as hub operators and commission agents, so intermediaries shift from price-setters to service providers.
•	Connectivity: Offline-first apps that sync when connectivity returns, plus SMS and IVR fallbacks.
•	Spoilage: Cold-chain-ready crates for high-value produce, a return-leg route priority for perishables, and a spoilage-compensation pool funded by a small platform levy.
•	Privacy: Consent-based data collection, encryption, DPDP Act 2023 compliance, and a published data-use policy.
Impact and Benefits
1. Potential Impact on the Target Audience
•	Farmers and FPOs: Farmers and FPOs receive a larger share of the consumer price, a fixed minimum price before harvest, and faster payment (within 24 hours instead of weeks).
•	Consumers: Households and institutional buyers pay lower prices because fewer margin layers are added and logistics costs are shared.
•	Bulk buyers: Bulk buyers such as canteens, schools, and retailers get reliable supply, traceable sourcing, and predictable pricing.
•	Rural youth: Local youth can become Sanchalak hub operators, earning income from collection and logistics services.
2. Benefits of the Solution
Category	Benefit
Economic	Higher farm-gate price; lower consumer price; lower logistics cost per unit; new service income for hub operators
Social	Reduced distress selling; stronger FPO institutions; digital inclusion through voice and regional-language access; women-led hub opportunities
Environmental	Fewer empty truck trips through return-leg sharing; less food wastage through shorter chains; reduced need for excess storage
Governance	Transparent price breakdown; auditable transaction trail; data for policymakers on demand, prices, and supply gaps
3. Measurable Targets (First Year Post-Pilot)
•	Farmer share of consumer price increased from the current level to at least 70% for participating commodities.
•	Retail price of participating commodities reduced by 10–15% against the district baseline.
•	Post-harvest losses reduced by 20% for pilot crops.
•	Payment cycle reduced from an average of 7–15 days to under 24 hours.
Research and References
The following sources inform the problem analysis, the proposed model, and the technical approach. Links should be verified and updated before final submission.
1.	Ministry of Consumer Affairs, Food & Public Distribution, Department of Food and Public Distribution: https://dfpd.gov.in
2.	Agricultural Marketing Information Network (AgMarkNet), Ministry of Agriculture & Farmers Welfare: https://agmarknet.gov.in
3.	National Agriculture Market (e-NAM) portal: https://enam.gov.in
4.	Small Farmers’ Agribusiness Consortium (SFAC), FPO promotion scheme: https://sfacindia.com
5.	Digital Agriculture Mission and Agri Stack, Ministry of Agriculture & Farmers Welfare: https://agristack.gov.in
6.	India Meteorological Department (IMD) weather data: https://mausam.imd.gov.in
7.	Bhashini, National Language Translation Mission: https://bhashini.gov.in
8.	Digital Personal Data Protection Act, 2023, Government of India: https://www.meity.gov.in
9.	Google OR-Tools, vehicle routing documentation: https://developers.google.com/optimization
10.	Prophet, time-series forecasting library, Meta: https://facebook.github.io/prophet
