# 🔐 Implementing Azure Conditional Access Control Policy

## 📌 Scenario
As an Azure Administrator, your goal is to strengthen security by preventing account access from high-risk countries using **Conditional Access policies** in Microsoft Entra ID.

This lab walks through creating a tenant, configuring a user, disabling security defaults, defining blocked locations, and enforcing a Conditional Access policy.

---

## 🎯 Objectives

- Create a Microsoft Entra External ID tenant
- Create a test user account
- Disable Security Defaults
- Configure Named Locations (by country/IP)
- Create a Conditional Access policy
- Test and validate access restrictions

---

## 🧱 Lab Environment

- Windows 11 (Admin access)
- Microsoft Azure Portal
- Microsoft Entra ID
- Microsoft Edge Browser
- Test Tenant + User

---

## 🏗️ Step 1: Create a New Tenant

1. Go to: https://portal.azure.com  
2. Navigate to **Microsoft Entra ID → Manage Tenants → Create**
3. Select **External ID Tenant**
4. Configure:
   - **Organization Name:** `comptia60393073`
   - **Domain:** `Domain60393073.onmicrosoft.com`
   - **Resource Group:** `RG1`
5. Click **Review + Create**

### 📸 Screenshot – Tenant Creation Success

<p align="center">
  <img src="Create-a-tenant-Click-here.png" width="750">
</p>

➡️ Click the link to switch into your new tenant.

---

## 👤 Step 2: Create a Test User

1. Navigate to **Microsoft Entra ID → Users → New User**
2. Configure:

| Field | Value |
|------|------|
| User Principal Name | TestUser |
| Display Name | TestUser |
| Password | CaTest-60393073 |

3. Create the user

---

## ⚙️ Step 3: Disable Security Defaults

1. Go to **Microsoft Entra ID**
2. Navigate to **Properties**
3. Select **Manage Security Defaults**
4. Set to **Disabled**

✅ This allows Conditional Access policies to be used.

---

## 🌍 Step 4: Create Named Location (Blocked Countries)

1. Go to **Security → Conditional Access → Named Locations**
2. Click **New Location**
3. Configure:
   - **Name:** `Blocked Countries By IP`
   - **Location Type:** Countries
4. Add the following countries:
   - Australia
   - Singapore
   - United Kingdom
   - United States

---

## 🚫 Step 5: Create Conditional Access Policy

1. Navigate to **Conditional Access → Policies → New Policy**
2. Configure:

### Policy Details
- **Name:** `Block - Locations - All Resources`

### Assignments
- **Users:** Select `TestUser`
- **Cloud Apps:** All resources
- **Conditions → Locations:**
  - Include: Any location
  - Exclude: None
  - Include Named Location: `Blocked Countries By IP`

### Access Control
- **Grant → Block Access**

3. Enable Policy → **On**

---

## 🧪 Step 6: Test the Policy

1. Open **Incognito/InPrivate browser**
2. Navigate to: https://portal.azure.com
3. Login using:
   - Username: `TestUser`
   - Password: `CaTest-60393073`

### 📸 Screenshot – Access Blocked

<p align="center">
  <img src="bcf3xvte.jpg" width="500">
</p>

🔒 Expected Result:
> "You cannot access this right now"

---

## 📊 Key Takeaways

- Conditional Access enhances Zero Trust security
- Named Locations allow geo-based restrictions
- Policies should be tested in **Report-Only mode** before enforcement (best practice)
- Always assign policies to **groups (production)** instead of individual users

---

## 🏁 Summary

✔️ Created a Microsoft Entra External ID tenant  
✔️ Configured a test user  
✔️ Disabled Security Defaults  
✔️ Defined blocked countries  
✔️ Deployed Conditional Access policy  
✔️ Successfully tested access restriction  

---

## 📚 CompTIA SecurityX Alignment

This lab demonstrates:

- **2.5 – Secure cloud capabilities in enterprise environments**
- Identity and Access Management (IAM)
- Conditional Access & Zero Trust enforcement
- Risk-based authentication controls
