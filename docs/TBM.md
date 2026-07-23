# TBM Taxonomy Mapping for Azure FinOps

This document defines how the **FOCUS dataset** aligns with the **TBM taxonomy**.  
It provides a consistent framework for reporting, chargeback, and showback across Finance, Engineering, and Business Units.

---

## TBM IT Towers

| **TBM Tower** | **FOCUS Column(s)** | **Example Azure Service** | **Driver** |
|---------------|----------------------|---------------------------|------------|
| Compute       | ServiceCategory = Compute | Virtual Machines, AKS | CPU hours |
| Storage       | ServiceCategory = Storage | Blob Storage, Managed Disks | GB stored |
| Network       | ServiceCategory = Network | Bandwidth, Load Balancer | GB transferred |
| End‑User      | ServiceCategory = EndUser | Windows 365, Intune | License count |
| Applications  | ServiceCategory = SaaS | Power BI, Dynamics 365 | License count |

---

## Cost Perspectives

FOCUS provides three cost perspectives, aligned with TBM reporting needs:

- **ActualCost** → Matches invoice values for Finance reconciliation.  
- **AmortizedCost** → Spreads reservation/savings plan costs for Engineering visibility.  
- **EffectiveCost** → Shows net cost after discounts/credits for optimization reporting.  

---

## Business Unit Mapping

Business Units are derived from **tags** and subscription hierarchy:

- `CostCenter` → Finance alignment.  
- `BU` → Business Unit ownership.  
- `Owner` → Resource accountability.  

Azure Policy enforces these tags to ensure consistent mapping.

---

## Governance Notes

- All exports must be in **FOCUS schema**.  
- Dashboards must report against **TBM towers**.  
- Chargeback/showback must use **AmortizedCost** for BU allocation.  
- Finance reconciliation must use **ActualCost**.  
- Optimization reports should highlight **EffectiveCost** savings opportunities.

---

## 🎯 Purpose

This TBM.md ensures that **Azure FinOps reporting is consistent, auditable, and aligned with industry standards**.  
It is the foundation for Power BI dashboards, cost allocation, and recommendation workflows.
