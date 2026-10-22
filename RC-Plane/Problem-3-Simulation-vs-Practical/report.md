# Problem 3 — Simulation vs Practical Development

## 1. Objective and design decision

The objective is to develop a functional RC aircraft for a national aeromodelling competition under limited time, budget and resources.

**Recommendation: use a simulation-informed, prototype-led hybrid workflow.** Analytical calculations and simulation should identify promising configurations and prevent avoidable design errors. Physical prototypes should then be used to verify actual mass, propulsion performance, structural integrity, control response and flight behaviour.

A simulation-only strategy is insufficient because its predictions depend on assumptions, model fidelity and input accuracy. A prototype-only strategy can reveal real-world problems but may waste materials and time on avoidable design mistakes. Combining both methods provides a practical balance between engineering confidence, development speed and cost.

The proposed aircraft is assumed to be a conventional, electrically powered, single-motor fixed-wing RC aircraft. Exact dimensions, competition rules, budget and component specifications are not supplied, so no aircraft performance or cost figures are claimed here.

## 2. Simulation-led versus prototype-led development

| Criterion | Simulation-led approach | Prototype-led approach | Recommended use |
|---|---|---|---|
| Cost | Software and analysis may be inexpensive, but specialist tools and computing can add cost | Requires materials, components, workshop access and possible replacement parts | Use free or accessible tools before committing to hardware |
| Time | Can evaluate multiple configurations rapidly after the model is established | Each build, repair and physical test consumes time | Simulate major design choices; prototype early |
| Accuracy | Depends on assumptions, input data, numerical methods and model fidelity | Directly reflects the tested hardware and conditions, but measurements have uncertainty | Cross-check predictions with measurements |
| Iteration speed | Fast for geometry and parameter sweeps; slow when models require substantial setup | Fast for simple modifications, but rebuilding can be expensive | Use simulation for broad exploration and prototypes for critical questions |
| Failure detection | Can identify predicted aerodynamic, structural or performance problems within the model's scope | Reveals assembly defects, vibration, real control problems, electrical faults and unexpected interactions | Use both methods at subsystem and aircraft levels |
| Final performance | Predicts performance under modelled conditions; cannot guarantee real flight performance | Demonstrates actual performance for the tested configuration and conditions | Accept the design only after requirements are verified in relevant tests |

Simulation is especially valuable when a design change is expensive to build repeatedly. Physical testing is essential when the outcome depends on manufacturing quality, real component behaviour or interactions that are difficult to model accurately.

Neither method is universally more accurate. A well-controlled experiment may still have measurement errors, while a carefully validated model may provide useful predictions beyond the limited conditions already tested.

## 3. Proposed development workflow

The project should proceed through short, documented design-build-test iterations.

```text
Define mission and competition requirements
                  |
                  v
Set measurable acceptance criteria
                  |
                  v
Preliminary sizing and hand calculations
                  |
                  v
CAD layout + aerodynamic/structural estimates
                  |
                  v
Select components and estimate mass
                  |
                  v
Build a low-cost prototype
                  |
                  v
Inspect structure, controls and electrical system
                  |
                  v
Ground tests and controlled flight tests
                  |
                  v
Compare predictions with measurements
                  |
                  v
Identify largest discrepancy or risk
                  |
                  v
Modify one major variable at a time
                  |
                  +------> Repeat tests
                  |
                  v
Verify requirements and freeze final design
```

### Stage 1 — Define requirements

Establish measurable requirements for take-off, controllability, endurance or mission duration, payload if required, structural integrity and budget. Identify competition rules and environmental conditions.

### Stage 2 — Perform preliminary calculations

Estimate wing loading, stall speed, required thrust, battery energy, expected take-off mass and centre-of-gravity range. Use these estimates to reject obviously unsuitable configurations before construction.

### Stage 3 — Model and select components

Use a CAD package for geometry and packaging. Use an appropriate aerodynamic tool to estimate lift, drag and stability trends. Check structural load paths and component compatibility. Record assumptions and identify model limitations.

### Stage 4 — Build and inspect

Construct the prototype and measure its actual mass and centre of gravity. Check wing alignment, control-surface movement, linkage security, motor mounting, propeller clearance and electrical connections.

### Stage 5 — Conduct ground and flight tests

Perform appropriate control-direction, radio-link, motor, battery and structural checks before flight. Begin with controlled, low-risk tests in a suitable legal location, following the aircraft and propulsion system's safety requirements. Increase the test envelope gradually rather than attempting aggressive manoeuvres immediately.

### Stage 6 — Refine and verify

Compare measured and predicted values, investigate discrepancies, modify the design and repeat relevant tests. Freeze the final configuration only when the required performance and safety criteria have been demonstrated.

## 4. Parameters to simulate and verify physically

### Parameters suitable for simulation

1. **Lift and drag:** estimate lift coefficient, drag coefficient and lift-to-drag ratio across the intended operating range. Results depend on Reynolds number, geometry and model limitations.
2. **Stability and control trends:** estimate static stability, pitching moment, centre-of-gravity sensitivity and control effectiveness using an appropriate aircraft model.
3. **Structural response:** estimate stress and deflection under defined load cases using a structural model with justified material properties, constraints and loads.

Other useful analyses include wing loading, estimated stall speed, propulsion matching and battery-energy requirements.

### Parameters requiring physical verification

1. **Actual mass and centre of gravity:** measure the completed aircraft in its flight-ready configuration, including battery and payload.
2. **Propulsion performance:** verify motor operation, current draw, battery voltage under load and, where suitable equipment is available, static thrust. Use component ratings and safe test procedures.
3. **Control and flight behaviour:** verify control directions, linkage travel, radio response, trim, take-off behaviour and stability during controlled flight testing.

Additional physical checks should include structural integrity, wing alignment, vibration, battery temperature and actual flight duration.

Simulation and physical testing answer different questions. For example, a predicted centre of gravity is only as reliable as the mass and position inputs; the finished aircraft must still be measured.

## 5. Validating simulation against measurements

Verification checks whether the design meets its specified requirements. Validation checks whether the model and design adequately represent the intended real-world behaviour. For a credible engineering submission, both are necessary.

The validation process should be:

1. **Define the quantity being compared.** Choose a measurable parameter, such as total mass, static thrust, current draw or flight duration.
2. **Match the conditions.** Use the same aircraft configuration, battery state, payload, environmental conditions and measurement definitions wherever practical.
3. **Record measurement uncertainty.** Document the instrument, resolution, repeatability and important environmental effects.
4. **Compare prediction with observation.** Calculate the difference and, where the reference value is meaningful and non-zero, the percentage error.

For a predicted quantity \(x_p\) and measured quantity \(x_m\),

\[
\text{Absolute error}=|x_m-x_p|
\]

\[
\text{Percentage error}
=\frac{|x_m-x_p|}{|x_p|}\times100\%
\]

The percentage-error expression is unsuitable when the prediction is zero or very close to zero; use absolute error and measurement uncertainty instead.

5. **Investigate discrepancies.** Check incorrect input values, simplified physics, manufacturing tolerances, sensor error, model convergence and mismatched test conditions.
6. **Update and retest.** Correct the model or design where justified, then compare it with an independent measurement or repeat test.

A model should not be declared validated merely because one predicted value matches one measurement. Validation should cover the relevant operating range and important failure modes. For low-Reynolds-number aircraft analysis, for example, aerodynamic predictions should be treated cautiously when separation or stall is not represented reliably.

## 6. Diagnostic plan: the simulated aircraft performs well but cannot take off

A failed take-off does not immediately prove that the aerodynamic simulation was wrong. The cause may be an incorrect model input, a construction defect, inadequate propulsion, a control problem or unsuitable test conditions.

| Possible cause | Why it prevents take-off | Diagnostic check |
|---|---|---|
| Actual mass exceeds the design estimate | Increases required lift and stall speed | Weigh the flight-ready aircraft and compare with the design mass |
| Centre of gravity is too far aft or forward | Can cause instability, excessive trim demand or difficulty rotating | Measure CG against the specified safe range for the actual design |
| Insufficient thrust or incorrect propeller | May prevent acceleration to the required flying speed | Check propeller specification, motor operation, battery voltage under load and thrust where measurable |
| Excessive drag or poor alignment | Reduces acceleration and may create asymmetric forces | Inspect wing alignment, surface defects, landing gear and protrusions |
| Incorrect wing incidence or control setup | Can produce inadequate lift, excessive nose-down behaviour or premature stall | Inspect geometry and control-surface directions and neutral positions |
| Control or radio failure | Prevents appropriate pitch or directional control | Perform approved control-direction, range and linkage checks |
| Incorrect simulation assumptions | Predicted performance may not match the real configuration | Recheck mass, airfoil data, Reynolds number, geometry and propulsion inputs |
| Ground friction or unsuitable launch surface | Reduces acceleration during the take-off roll | Inspect wheel alignment, surface condition and rolling resistance |

### Systematic diagnostic sequence

**Step 1 — Make the aircraft safe.** Disarm the propulsion system before handling the propeller or inspecting linkages. Do not repeat full-power attempts until the cause is better understood.

**Step 2 — Check mass and geometry.** Measure the flight-ready mass, CG and wing alignment. Compare them against the design assumptions.

**Step 3 — Verify the control system.** Confirm control directions, neutral positions, linkage security and radio operation. Follow the manufacturer's and club's safety procedures.

**Step 4 — Check propulsion.** Confirm the motor, propeller, battery and electronic speed controller are compatible and functioning correctly. Compare measured electrical and thrust data, where available, with the expected values.

**Step 5 — Check the take-off environment.** Verify the surface, wind, runway length and operating procedure are suitable for the design.

**Step 6 — Revisit the model.** If hardware and setup checks pass, recalculate the required lift and speed, then investigate model assumptions and predicted thrust-to-weight performance.

**Step 7 — Change one variable at a time.** Document each adjustment and its effect. Avoid arbitrary changes that could mask the original fault or make the aircraft unsafe.

This sequence prioritises inexpensive, observable causes before more complex analysis and reduces the risk of damaging the prototype through repeated failed attempts.

## 7. Four-week development schedule (bonus)

The schedule below is a proposed plan, not a record of work already completed. It assumes a small team, access to basic fabrication facilities and suitable test conditions.

| Week | Main activities | Deliverable and contingency |
|---|---|---|
| 1 — Requirements and preliminary design | Review competition rules; define measurable requirements; perform initial sizing; compare candidate configurations; select a baseline | Requirements list, initial calculations and design review. Reserve the final day for correcting major sizing or component-compatibility issues |
| 2 — Detailed design and fabrication | Complete CAD and component layout; estimate mass and CG; procure components; fabricate the first airframe | Prototype and inspection checklist. Allow time for delivery delays and fabrication rework |
| 3 — Integration and initial testing | Assemble propulsion and controls; verify CG and control directions; perform ground tests and initial controlled flight tests when safe and feasible | Test log and discrepancy list. Reserve at least one test session for repairs or repeat measurements |
| 4 — Refinement and final verification | Address the most important failure modes; repeat tests; compare results with predictions; document limitations and final configuration | Final test report, validated measurements and submission package. Keep the last two days as contingency where the calendar permits |

The highest-risk items should be addressed early: component availability, actual aircraft mass, centre of gravity, propulsion compatibility and access to a safe test area. If flight testing is delayed by weather or safety concerns, use the time for ground verification and documentation; do not claim flight results that were not obtained.

## 8. Conclusion

A simulation-informed, prototype-led hybrid process is the most defensible approach for a small RC-aircraft development project with limited resources. Simulation narrows the design space, supports quantitative trade-offs and reduces avoidable fabrication work. Physical prototypes expose manufacturing errors, component limitations and real aerodynamic behaviour that simplified models may miss.

The development process should therefore combine preliminary calculations, appropriately scoped simulation, early prototyping, safe ground and flight testing, and systematic comparison between predictions and measurements. The final design should be accepted on demonstrated performance against defined requirements, not on simulation results alone.

## References

1. NASA, *NASA Systems Engineering Handbook*, especially the sections on product realisation, verification and validation.  
   https://www.nasa.gov/reference/systems-engineering-handbook/

2. NASA, *5.3.2 Product Verification Guidance*. Guidance on verification approaches, testing and analysis.  
   https://www.nasa.gov/reference/5-0-product-realization/

3. XFLR5, official project website and documentation. Describes low-Reynolds-number airfoil, wing and aircraft analysis capabilities and includes comparisons of predictions with measurements.  
   https://www.xflr5.com/

4. XFLR5 documentation, *Theoretical Limitations and Shortcomings*. Explains why results should be used to study trends and sensitivity within appropriate modelling limits rather than assumed to be exact.  
   https://www.xflr5.tech/docs/Part%20IV%3A%20Limitations.pdf

5. Robotronics Club, IIT Mandi, *Project X Selection Tasks — Problem 3: Simulation vs Practical Development*. Assignment requirements and deliverables.  
   https://github.com/the-robotronics-club/Project-X-Selection-Tasks/blob/main/RC-Plane/03_simulation_vs_practical.md
