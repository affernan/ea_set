<p align="center">
  <strong>EA_SET</strong><br />
  Scenario set for electric aircraft scheduling, charging, and spare battery planning experiments.
</p>

<p align="center">
  <img alt="CSV-style data" src="https://img.shields.io/badge/data-CSV--style-2f6f4e" />
  <img alt="Instances 13" src="https://img.shields.io/badge/instances-13-444444" />
</p>

<p align="center">
  <code>Electric Aircraft</code> | <code>Scheduling</code> | <code>Charging</code> | <code>Battery Planning</code>
</p>

---

`ea_set` contains planning instances for electric aircraft operations. Each file describes charging infrastructure, spare battery availability, aircraft flight schedules, departure and arrival times, destinations, and state-of-charge values.

The repository is data-only. It does not provide a parser, solver, runtime, or validation script.

## Product Surface

| Area | Contract |
| --- | --- |
| Runtime | None; static scenario files |
| Data format | Human-readable CSV-style text files |
| Data path | Solver or parser reads files directly from the repository |
| Storage | Git-tracked `.csv` files |
| Documentation | This README |
| Distribution | GitHub repository |

## Runtime Shape

```mermaid
flowchart LR
  researcher["Researcher"] --> repo["EA_SET"]:::primary
  repo --> files["13 scenario files"]
  files --> solver["Scheduling or planning model"]

  classDef primary fill:#2f6f4e,stroke:#173927,color:#ffffff,stroke-width:2px
```

## Responsibilities

- Store electric aircraft scenario inputs in a readable, versioned form.
- Preserve infrastructure parameters for mega chargers, regular chargers, and spare batteries.
- Preserve flight-level information by aircraft, flight, destination, time, and state of charge.
- Leave parser and optimization-model behavior to downstream projects.

## How It Is Built

This repository is organized as a flat set of data files.

| File | Role |
| --- | --- |
| `EA_2_1.csv` through `EA_50_2.csv` | Scenario instances grouped by size and variant. |
| `EA_10_1_delay.csv` | Scenario variant that includes delay-specific data. |
| `README.md` | Repository description and data contract. |

## Platform and Service Dependencies

<table>
  <tr>
    <th>Service / Object</th>
    <th>Provider</th>
    <th>Usage</th>
    <th>Purpose</th>
  </tr>
  <tr>
    <td><code>EA_*.csv</code></td>
    <td>Repository files</td>
    <td>Read by an external parser, optimization model, or experiment script.</td>
    <td>Provides reproducible aircraft charging and battery-planning inputs.</td>
  </tr>
</table>

## File Structure

Each instance includes:

- Number of mega chargers.
- Number of regular chargers.
- Number of spare batteries.
- Flight rows with aircraft, flight identifier, destination, departure time, arrival time, and state of charge.

The files use aligned text tables rather than a strict comma-separated schema. Downstream parsers should validate the expected section headers before batch processing.

## Verification

No automated tests are defined for this repository. Recommended manual verification is to inspect a representative instance and confirm that a downstream parser can read all expected sections.

## Secret Handling

The repository contains public planning data only. Do not commit private operational schedules or credentials.
