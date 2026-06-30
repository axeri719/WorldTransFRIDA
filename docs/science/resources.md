### Overview

The Resources module covers two material-and-emissions systems that sit at the interface between the human economy and the carbon cycle: carbon capture and storage (CCS), and the production and stock of concrete. The concrete sub-model is a fully developed stock-flow system driven by demand, building lifecycle, deterioration, and policy. The CCS sub-model is **preliminary and not production ready** — an area of active development (see below). Both draw fossil-fuel and bioenergy emissions from the Emissions and Energy modules, take policy levers from the Government Regulations module, and return carbon flows that feed back into the carbon cycle.

### Carbon capture and storage (preliminary)

!!! warning "Preliminary — not production ready"
    The CCS sub-model is an early placeholder and an area of active development. It is wired into the rest of FRIDA but its mechanism is deliberately simple, and in the base configuration its policy levers are set to zero, so it captures and stores no carbon. Results should not rely on it until it is further developed.

### Concrete and process emissions

The Concrete sub-model tracks the global in-use stock of concrete across four stocks: new and old residential-and-service buildings, and new and old infrastructure. Demand for buildings is built from desired useful floor area, a logarithmic function of GDP per person scaled by population and converted to concrete via a concrete-per-floor-area intensity. Infrastructure demand is a regression on population, GDP per capita, and their interaction. In each case, the gap between desired and installed stock drives a construction flow, smoothed over an adjustment time.

Concrete moves through a lifecycle: new structures age into the old stock at a cutpoint of half their average lifetime, old structures are eventually decommissioned, and both deteriorate continuously through wear. New construction and maintenance (replacing deteriorated material) together constitute total yearly concrete use.

Each tonne of concrete produced carries process and material CO₂ emissions, computed from construction-plus-maintenance throughput times a CO₂ intensity specific to building versus infrastructure mixes. These emissions feed the carbon cycle. The model represents the production-side emissions of cement and concrete; it does not credit any carbonation re-uptake as a CO₂ sink — carbonation appears only as a corrosion mechanism that, with chloride exposure, shortens concrete service life.

### Climate feedbacks and coupling

Rising surface temperature shortens concrete service life, accelerating aging, deterioration, and the replacement construction (and its emissions) needed to hold stocks. Extreme-weather storm damage, valued from coastal-asset damages in the Climate module, adds to deterioration of older structures. Concrete production in turn adds process and material CO₂ to the carbon cycle, closing a loop to warming. (CCS would also couple to the carbon cycle, but is inactive in the base configuration — see above.)