# FOCUS Dataset Reference for Azure FinOps

This document defines the **FOCUS dataset columns** and explains how they align with **TBM taxonomy** for consistent reporting and governance.

---

## Core Columns

| **FOCUS Column** | **Purpose** | **TBM Alignment** |
|------------------|-------------|-------------------|
| BillingAccountId | Identifies billing account | Finance reconciliation |
| BillingPeriod    | Invoice period | Finance reconciliation |
| ResourceId       | Unique Azure resource | Resource accountability |
| ResourceName     | Human-readable name | BU ownership |
| ServiceCategory  | High-level service grouping | TBM Towers (Compute, Storage, Network, End‑User, Applications) |
| MeterCategory    | Usage metric grouping | TBM Drivers (CPU hours, GB storage, bandwidth) |
| UsageAmount      | Quantity consumed | Driver values |
| UnitOfMeasure    | Unit for usage amount | Driver normalization |
| ActualCost       | Invoice cost | Finance reconciliation |
| AmortizedCost    | Reservation/Savings Plan spread | BU chargeback/showback |
| EffectiveCost    | Net cost after discounts/credits | Optimization reporting |
| Currency         | Currency of billing | Finance reconciliation |
| Tags             | Metadata (CostCenter, BU, Owner) | Business Unit mapping |

---

## Cost Perspectives

- **ActualCost** → Matches invoice values for Finance.  
- **AmortizedCost** → Spreads reservation/savings plan costs for BU allocation.  
- **EffectiveCost** → Shows net cost after discounts/credits for optimization.  

---

## Tagging Standards

FOCUS dataset supports **resource tags** for mapping into TBM taxonomy:

- `CostCenter` → Finance alignment.  
- `BU` → Business Unit ownership.  
- `Owner` → Resource accountability.  

Azure Policy enforces these tags to ensure consistent mapping.

---

## Governance Notes

- All exports must be created in **FOCUS schema** using PowerShell (`New-FinOpsCostExport`).  
- Dashboards must report against **TBM towers** using `ServiceCategory`.  
- Chargeback/showback must use **AmortizedCost**.  
- Finance reconciliation must use **ActualCost**.  
- Optimization reports should highlight **EffectiveCost** savings opportunities.

---

## Purpose

This FOCUS.md ensures that **Azure FinOps reporting is standardized, auditable, and aligned with TBM taxonomy**.  
It is the schema reference for PowerShell automation, Power BI dashboards, and recommendation workflows.
