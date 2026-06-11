# ✈️ Travel & Hospitality Analytics — Power BI Portfolio Project

## 📌 Project Overview
A full end-to-end Travel & Hospitality analytics project built with **Power Query** and **Power BI**, covering hotel performance, guest experience, flight analytics, and revenue management across 13 real-world datasets.

---

## 📂 Datasets Used

| Table | Rows | Type | Description |
|-------|------|------|-------------|
| Hotel Bookings | 2,500 | Fact | Hotel reservations |
| Payments | 2,452 | Fact | Payment transactions |
| Guest Reviews | 1,431 | Fact | Guest ratings & comments |
| Flight Bookings | 980 | Fact | Flight reservations |
| Service Requests | 758 | Fact | Guest service requests |
| Customers | 800 | Dimension | Customer master data |
| Hotels | 100 | Dimension | Hotel reference data |
| Flights | 200 | Dimension | Flight reference data |
| Rooms | 300 | Dimension | Room types & pricing |
| Airports | 7 | Dimension | Airport reference data |
| Promotions | 4 | Dimension | Promotional offers |
| Amenities | 7 | Dimension | Hotel amenities list |
| Hotel Amenities | 504 | Bridge | Hotels ↔ Amenities mapping |

**Total: 9,043 rows of Travel & Hospitality data**

---

## 🔧 Tools & Skills

- **Power Query** — 13-table import, cleaning, custom columns
- **Power BI** — Complex Star Schema, DAX measures, custom theme
- **Custom JSON Theme** — Professional blue hospitality styling
- **DAX** — CALCULATE, SUM, AVERAGE, COUNTROWS, DIVIDE
- **Hospitality KPIs** — ADR, RevPAR, Avg Rating, Occupancy

---

## 🧹 Data Cleaning (Power Query)

- Changed all date columns to Date type
- Applied Text.Trim to all text columns
- Replaced null values with "Unknown" or 0
- Removed errors with Remove Rows → Remove Errors
- Added calculated columns:

**Hotel Bookings:**
- `Length of Stay` = CheckOutDate - CheckInDate
- `Booking Status Label` = ✅ Confirmed / ❌ Cancelled / 🏁 Completed / ⏳ Pending
- `Season` = ☀️ Summer / ❄️ Winter / 🌸 Spring / 🍂 Autumn

**Payments:**
- `Amount Band` = Low / Medium / High

**Guest Reviews:**
- `Sentiment Label` = 😊 Positive / 😐 Neutral / 😞 Negative

**Flights:**
- `Flight Duration (hrs)` = ArrivalTime - DepartureTime
- `Price Band` = Budget / Standard / Premium

---

## 🗂️ Data Model — Star Schema

**Date Table:** 2020–2026

**Relationships via Date:**
- Date → Hotel Bookings (BookingDate)
- Date → Payments (PaymentDate)
- Date → Guest Reviews (ReviewDate)
- Date → Flight Bookings (BookingDate)
- Date → Customers (JoinDate)

**Relationships via Keys:**
- Customers → Hotel Bookings (CustomerID)
- Customers → Flight Bookings (CustomerID)
- Hotels → Hotel Bookings (HotelID)
- Hotels → Hotel Amenities (HotelID)
- Rooms → Hotel Bookings (RoomID)
- Hotel Bookings → Payments (BookingID)
- Hotel Bookings → Guest Reviews (BookingID)
- Hotel Bookings → Service Requests (BookingID)
- Flights → Flight Bookings (FlightID)
- Amenities → Hotel Amenities (AmenityID)

---

## 📊 DAX Measures

```dax
Total Bookings        = COUNTROWS('Hotel Bookings')
Total Revenue         = SUM('Payments'[Amount])
ADR                   = DIVIDE([Total Revenue], SUM('Hotel Bookings'[Length of Stay]))
Avg Length of Stay    = AVERAGE('Hotel Bookings'[Length of Stay])
Avg Rating            = AVERAGE('Guest Reviews'[Rating])
Total Reviews         = COUNTROWS('Guest Reviews')
Total Service Requests= COUNTROWS('Service Requests')
Total Flight Bookings = COUNTROWS('Flight Bookings')
Avg Flight Price      = AVERAGE('Flights'[Price])
Total Payments        = COUNTROWS('Payments')
Avg Payment Amount    = AVERAGE('Payments'[Amount])
```

---

## 📈 Dashboards

### 1️⃣ 🏨 Hotel Performance Analytics
- KPI Cards: Total Bookings · Total Revenue · ADR · Avg Rating
- Top Hotels by Revenue (Bar Chart)
- Bookings by Status (Pie Chart)
- Bookings by Season (Bar Chart)
- Revenue Trend by Month (Line Chart)
- City Slicer

### 2️⃣ ⭐ Guest Experience & Reviews
- KPI Cards: Avg Rating · Total Reviews · Total Service Requests
- Sentiment Distribution (Pie Chart)
- Rating by Hotel (Bar Chart)
- Service Requests by Type (Bar Chart)
- Reviews Trend by Month (Line Chart)
- Sentiment Slicer

### 3️⃣ ✈️ Flight Analytics
- KPI Cards: Total Flight Bookings · Avg Flight Price
- Bookings by Airline (Bar Chart)
- Price Band Distribution (Bar Chart)
- Top Routes by Origin (Bar Chart)
- Flight Bookings Trend (Line Chart)
- Airline Slicer

### 4️⃣ 💰 Revenue & Payments Analytics
- KPI Cards: Total Revenue · Avg Payment Amount · Total Payments
- Revenue by Payment Method (Bar Chart)
- Payment Status Distribution (Pie Chart)
- Amount Band Distribution (Bar Chart)
- Revenue Trend by Month (Line Chart)
- Payment Method Slicer

---

## 💡 Key Business Insights

1. **Vistara is the top airline** — leading in flight bookings across all routes, indicating strong brand preference among travelers.

2. **Net Banking is the most popular payment method** — closely followed by other methods, suggesting a digitally savvy customer base with no single dominant payment preference.

3. **Spring is the peak booking season** — hotels experience highest demand during Spring, requiring dynamic pricing strategies during this period.

4. **Room Service dominates service requests** — the most common guest request, highlighting the importance of efficient in-room dining operations.

5. **Average Rating is 2.96/5** — below the 3.5 benchmark, indicating significant room for improvement in guest satisfaction across properties.

6. **ADR of 7.45K with 73.56M Total Revenue** — strong revenue performance driven by premium room pricing rather than volume.

---

## 🧠 Lessons Learned

- 13-table Star Schema requires careful relationship planning — Bridge tables (Hotel Amenities) need both ends connected.
- All Payments had "Success" status — in production, filtering by status adds value only when multiple status types exist.
- Synthetic data produces balanced distributions — real hospitality data shows more variance in seasonality and payment methods.
- Custom JSON Theme applied consistently across all 4 pages improves visual coherence significantly.
- ADR (Average Daily Rate) is calculated as Revenue ÷ Total Nights, not Revenue ÷ Bookings — an important hospitality-specific distinction.

---

## 👤 Author
**AbdelHassib Essayad**
Data Management Analyst & Accounting Specialist | 15+ Years Experience
Power BI · Power Query · DAX · Travel & Hospitality Analytics

🔗 [GitHub Portfolio](https://github.com/hassib-essayad)
📧 essayad@gmail.com
