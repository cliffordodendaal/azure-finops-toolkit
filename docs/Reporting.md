# Reporting with Power BI

This document explains how to connect **Azure Cost Management exports** (FOCUS schema) into **Power BI**, and how to build common FinOps reports aligned with **TBM taxonomy**.

---

## Connecting Power BI to Azure Cost Data

### Option 1: API Connection
- Use the **Azure Cost Management REST API**.
- Authenticate with `Connect-AzAccount` and `Get-AzAccessToken`.
- Query cost data in FOCUS schema using PowerShell:
  ```powershell
  New-FinOpsCostExport -Name "FOCUSExport" -Schema "FOCUS"
