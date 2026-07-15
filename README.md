# Electric Aircraft Scenario Set

This repository contains scenario files for electric aircraft operations with charging infrastructure and spare battery sizing data.

Each file describes a planning instance with infrastructure parameters and flight schedules. The instances can be used to test models or algorithms for aircraft assignment, charging operations, battery availability, and related scheduling decisions.

## Contents

The repository includes 13 CSV-style text files named by scenario size and variant, for example:

- `EA_2_1.csv`
- `EA_10_1.csv`
- `EA_10_1_delay.csv`
- `EA_50_2.csv`

## File Structure

Each instance includes:

- Number of mega chargers.
- Number of regular chargers.
- Number of spare batteries.
- Flight information by aircraft, flight identifier, destination, departure time, arrival time, and state of charge.

The files use a readable tabular layout rather than a conventional comma-separated schema. They should be parsed accordingly if used as input data.

## Suggested Use

These instances are intended for computational experiments involving electric aircraft scheduling and charging infrastructure planning. Researchers may adapt parsers to the exact layout required by their optimization model.
