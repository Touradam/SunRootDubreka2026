# Project Context

SunRoots is launching the Dubreka 2026 solar irrigation pilot to improve food security, climate resilience, and energy access for a youth farming community in Guinea. This document is the operational and engineering baseline for the web app and field execution teams.

## Mission & Stakeholders

### Mission
- Replace labor-intensive manual watering with a durable, low-cost, and replicable solar-powered irrigation system.

### Stakeholders
- **SunRoots:** Program owner and non-profit implementing partner.
- **Beneficiary farmers:** Youth farmers managing a 1-hectare community farm (cassava, pineapples, bananas).
- **Technical advisor (Adama Toure):** Remote renewable energy engineer providing system design and oversight.
- **Local contractors and technicians:** Installation and maintenance workforce operating on-site.

### Primary user groups for the app
- Field installers who must verify electrical compatibility before wiring.
- Supervisors who need a standardized quality checklist during installation.
- Farmers/maintenance teams who log recurring upkeep activities.

## Site Environment

### Location
- Dubreka, Kindia Region, Guinea
- Coordinates: `9.7898126, -13.4745297`
- Terrain: Slopes of Mount Kakoulima with elevation differences between water source and field/tank zones.

### Climate and operating conditions
- High heat exposure.
- Heavy monsoon rains (June to October).
- Severe dry and dusty season (November to May).
- Muddy access and difficult working conditions during wet months.
- Potential partial shading from nearby vegetation.
- No reliable internet connectivity expected during normal field operations.

## Technical Architecture

### System concept
- **Design philosophy:** Direct-drive solar pumping with no batteries.
- **Energy strategy:** Store solar energy as elevated water, not chemical battery capacity.

### Core hardware chain
1. **Water source:** Surface-water retention basin (3 to 5 m deep) on a permanent stream in the lowland.
2. **Pump:** Ennos 1.5 HP (1.1 kW) DC sunlight surface progressive cavity pump, suspended in basin.
3. **PV array:** Three 500 W to 600 W monocrystalline modules wired in series (`3S`) at hilltop.
4. **Controller:** Integrated Ennos MPPT controller.
5. **Water storage:** Elevated hilltop tank.
6. **Distribution:** Gravity-fed drip irrigation from tank to crops downslope.

## Critical Electrical Constraints

The following constraints are non-negotiable engineering safety rules for procurement and installation:

1. **Absolute MPPT voltage ceiling:** The Ennos controller input must never exceed `160 V` open-circuit under any condition.
2. **Panel selection rule for 3S array:** Because three modules are in series, each module must have `Voc < 53 V` to keep total series Voc below 160 V.
3. **Series string compliance:** Any candidate panel that violates the per-module Voc rule is disqualified.
4. **Protection requirement:** Install one DC breaker rated `18 A to 35 A` between PV array and controller for transient protection and safe maintenance isolation.
5. **Safety-first verification:** Electrical compatibility must be confirmed before purchasing or installing panels.

## Operational Workflows The App Must Support

1. **Panel compatibility safety check (pre-procurement):**
   - Enter local panel specifications.
   - Automatically evaluate compatibility with controller voltage constraints.
   - Return clear pass/fail decision and reason.

2. **Installation quality checklist (commissioning):**
   - Step-by-step checklist for wiring, breaker placement, mounting quality, and basic commissioning checks.
   - Standardized completion record for contractor accountability.

3. **Maintenance tracking (operations):**
   - Schedule and log routine tasks (panel cleaning, shading control, connector inspection, visual checks).
   - Preserve maintenance history to reduce long-term performance degradation.

## Non-Functional Requirements (Offline, Durability, Simplicity)

- **Offline-first operation:** All core functions must work without internet access.
- **Low-complexity UX:** Simple forms and clear pass/fail outputs for mixed technical literacy.
- **Field-ready resilience:** Support rugged conditions and intermittent device availability.
- **Data clarity:** Records should be readable and usable by both local teams and remote advisor.
- **Long-lifecycle support:** Tool should reinforce practices that keep system performance stable for 10+ years.

## Initial MVP Feature Priorities

Priority order is based on risk reduction and operational dependence:

1. **Panel compatibility safety checker (highest priority):**
   - Prevents controller damage from over-voltage panel choices.
   - Must be available before procurement and installation.

2. **Installation quality checklist:**
   - Standardizes workmanship and lowers commissioning failures.
   - Captures evidence of correct breaker placement and wiring sequence.

3. **Maintenance scheduler and logbook:**
   - Sustains long-term system output and reliability.
   - Enables advisor visibility into recurring field care.

## Implementation Guidance For Next Phase

- Build the first app module around the panel safety checker using the above electrical rules as hard validations.
- Keep architecture and data model compatible with adding checklist and maintenance modules next.
- Preserve offline capability from day one to match real site connectivity constraints.
