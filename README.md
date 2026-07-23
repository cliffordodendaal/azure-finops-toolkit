# Clifford Odendaal - Azure FinOps Toolkit (Extended Fork)

This repository is a fork of [microsoft/finops-toolkit](https://github.com/microsoft/finops-toolkit), extended to provide:

- **TBM taxonomy alignment** — Canonical mapping of Azure resources into IT Towers, Drivers, and Business Units.
- **FOCUS dataset integration** — Standardized schema for cost and usage data, ensuring consistency across reports.
- **PowerShell automation** — Scripts for exports, transforms, reconciliation of actual vs amortized costs, and validated recommendation actions.
- **Power BI reporting** — Starter templates and guidance for chargeback, showback, invoice reconciliation, and MACC burn‑down.
- **Governance guardrails** — Azure Policy definitions and approval workflows for consistent tagging and controlled remediation.

## Repo Structure

- `/docs/` → TBM.md, FOCUS.md, Reporting.md, Recommendations.md  
- `/powershell/` → Exports.ps1, Transforms.ps1, Fixes.ps1, Recommendations.ps1  
- `/powerbi/` → Chargeback.pbit, Finance.pbit, MACC.pbit  
- `/governance/` → TagPolicy.json, ApprovalWorkflow.md  

## Getting Started

1. Install the FinOps Toolkit PowerShell module:
   ```powershell
   Install-Module -Name FinOpsToolkit
   Connect-AzAccount


### License

Copyright © Microsoft Corporation. All rights reserved.

Licensed under the [MIT license](LICENSE).
