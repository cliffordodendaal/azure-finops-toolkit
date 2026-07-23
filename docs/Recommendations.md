# Recommendations Workflow

This document defines how **Azure Advisor** and **Cost Management recommendations** are validated and actioned within the FinOps framework.  
It ensures that optimization steps are consistent, auditable, and aligned with **TBM taxonomy** and **FOCUS dataset** reporting.

---

## Types of Recommendations

| **Category** | **Examples** | **FOCUS/TBM Alignment** |
|--------------|--------------|--------------------------|
| Right‑sizing | Resize VMs, AKS nodes | Compute Tower, AmortizedCost |
| Cleanup      | Delete unattached disks, idle IPs | Storage/Network Towers |
| Reservations | Buy Reserved Instances, Savings Plans | AmortizedCost allocation |
| Governance   | Enforce tags, policy compliance | BU mapping via tags |
| Optimization | Apply discounts, credits | EffectiveCost reporting |

---

## Validation Rules

Before actioning any recommendation:

1. **Check TBM alignment**  
   - Does the resource map correctly to a TBM tower?  
   - Are tags (`CostCenter`, `BU`, `Owner`) present?  

2. **Check cost perspective**  
   - Finance dashboards → use `ActualCost`.  
   - BU chargeback → use `AmortizedCost`.  
   - Optimization → use `EffectiveCost`.  

3. **Check business approval**  
   - BU owner must approve right‑sizing or cleanup.  
   - Finance must approve reservation purchases.  

---

## PowerShell Automation

Example workflow to action validated recommendations:

```powershell
# Connect to Azure
Connect-AzAccount

# Get recommendations
$recs = Get-AzAdvisorRecommendation

# Filter only validated recommendations
$validRecs = $recs | Where-Object {
    $_.ResourceTags["BU"] -ne $null -and
    $_.Impact -eq "High"
}

# Action recommendations (example: resize VM)
foreach ($rec in $validRecs) {
    if ($rec.RecommendationType -eq "RightSize") {
        Resize-AzVM -ResourceId $rec.ResourceId -Size $rec.TargetSize
    }
}
