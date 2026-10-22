Problem 1: Airfoil Selection and Aerodynamic Analysis
1. Objective
This report investigates suitable airfoils for two RC aircraft with different mission requirements.

Aircraft A — Payload aircraft: Carry a useful payload while maintaining predictable, stable flight.

Aircraft B — Manoeuvrable aircraft: Perform turns, rolls and loops while maintaining adequate aerodynamic performance and control.

An airfoil is the cross-sectional shape of a wing. Its geometry affects lift, drag, pitching moment and flow separation. However, the performance of a complete aircraft also depends on wing area, wing loading, centre of gravity, tail design, control surfaces, structural strength and propulsion.

The report compares three candidate airfoils for each mission, establishes preliminary selections and identifies the further aerodynamic evidence needed to validate those selections.

2. Assumptions and Methodology
Because the actual RC aircraft dimensions and flight speed have not been provided, the following preliminary assumptions are used.

Parameter	Assumed value
Cruise airspeed	15 m/s
Mean wing chord	0.20 m
Air density	1.225 kg/m³
Dynamic viscosity of air	0.0000181 kg/(m·s)
Mach number	Approximately 0.044
Estimated Reynolds number	Approximately 203,000
These are assumed design values, not measurements of the actual aircraft.

Reynolds number calculation
Reynolds number is calculated as:

Re = (air density × airspeed × chord) / dynamic viscosity

Using the assumptions above:

Re = (1.225 × 15 × 0.20) / 0.0000181

Re ≈ 203,000

This estimate provides a preliminary condition for comparing airfoils. Actual Reynolds number will vary with airspeed and local wing chord. If the aircraft's dimensions or intended speed differ significantly from these assumptions, the comparison should be repeated.

Aerodynamic quantities
Lift depends on air density, airspeed, wing area and lift coefficient:

Lift = 0.5 × air density × airspeed² × wing area × lift coefficient

Drag is calculated similarly:

Drag = 0.5 × air density × airspeed² × wing area × drag coefficient

The lift-to-drag ratio is:

Lift-to-drag ratio = lift coefficient / drag coefficient

A higher lift-to-drag ratio indicates better aerodynamic efficiency at the operating condition being compared. It does not necessarily indicate the best maximum-lift or aerobatic performance.

A fair comparison should use the same Reynolds number and comparable lift coefficients. Stall behaviour should be assessed separately, because numerical predictions near stall may be unreliable.

3. Aircraft A: Maximum Payload and Predictable Flight
3.1 Design requirements
Aircraft A should generate sufficient lift to support its own weight and payload. It should also have acceptable drag at its intended cruising condition and predictable handling.

The following candidates are considered:

NACA 4412

Clark Y

Eppler E423

3.2 Candidate 1: NACA 4412
The NACA 4412 is a cambered airfoil. Under the standard NACA four-digit designation, its nominal geometry has:

Maximum camber: 4% of chord

Maximum camber location: 40% of chord from the leading edge

Maximum thickness: 12% of chord

Camber allows the airfoil to generate positive lift at zero geometric angle of attack under typical attached-flow conditions. This makes it a reasonable starting candidate for an aircraft that spends most of its flight in conventional forward flight.

Its moderate thickness may also provide useful depth for wing construction. However, structural strength depends on the spar, ribs, materials and construction method rather than thickness alone.

NASA has published experimental and calculated aerodynamic comparisons for the NACA 4412. One available NASA report presents lift and drag comparisons at a Reynolds number of 3,000,000. This is useful background evidence for the airfoil, but it is not a direct substitute for data at the estimated Reynolds number of 203,000.

Assessment: A reasonable baseline candidate, pending a comparison at the intended operating conditions.

3.3 Candidate 2: Clark Y
The Clark Y is a cambered airfoil with a relatively flat lower surface over much of its chord. Its geometry has historically been convenient for model-aircraft construction.

The geometry database used for this report lists approximately:

Maximum camber: 3.4% of chord

Maximum camber location: approximately 41.5% of chord

Maximum thickness: 11.7% of chord

A published low-Reynolds-number wind-tunnel investigation examined Clark Y performance between Reynolds numbers of 50,000 and 200,000. This range is relevant to small RC aircraft.

The study makes Clark Y a worthwhile candidate for further investigation. However, the existence of experimental data does not automatically establish that it performs better than NACA 4412 under the present assumptions. The corresponding lift and drag values must be extracted at a comparable Reynolds number and operating condition.

Assessment: A credible alternative, especially where practical wing construction and low-Reynolds-number performance are important.

3.4 Candidate 3: Eppler E423
The Eppler E423 is a highly cambered airfoil listed in airfoil-coordinate databases.

The geometry data available for this report indicates approximately:

Maximum camber: 10% of chord

Maximum camber location: approximately 44% of chord

Maximum thickness: 12.5% of chord

Its comparatively large camber makes it worth investigating for a lift-oriented aircraft. However, greater camber does not automatically guarantee better payload performance. Drag, pitching moment, stall behaviour and the actual operating lift coefficient must also be considered.

Available online aerodynamic estimates for E423 are model-based and should not be presented as experimental measurements. Their conditions and limitations must be checked before using numerical values in a final ranking.

Assessment: A relevant high-camber candidate, but its suitability must be established through a matched-condition comparison.

3.5 Comparison of Aircraft A candidates
Criterion	NACA 4412	Clark Y	Eppler E423
Maximum camber	4%	Approximately 3.4%	Approximately 10%
Maximum thickness	12%	Approximately 11.7%	Approximately 12.5%
General geometry	Moderately cambered	Cambered, relatively flat lower surface	Highly cambered
Lift at zero geometric angle	Positive lift generally expected	Positive lift generally expected	Positive lift generally expected
Maximum lift coefficient at Re ≈ 203,000	Not verified here	Experimental data exists in a relevant Reynolds-number range; exact matched value not extracted	Not verified here
Drag at a common lift coefficient	Not verified here	Not verified here	Not verified here
Lift-to-drag ratio at a common condition	Not verified here	Not verified here	Not verified here
Stall behaviour at the assumed condition	Requires matched data	Requires detailed experimental data	Requires matched data
Preliminary suitability	Balanced baseline candidate	Practical alternative	High-camber alternative worth testing
The table deliberately separates known geometry from aerodynamic performance that has not been verified under matching conditions.

3.6 Preliminary selection for Aircraft A: NACA 4412
NACA 4412 is selected provisionally because it provides a moderate-camber, moderate-thickness baseline with published aerodynamic references.

This is a defensible starting point, not proof that NACA 4412 is the best airfoil for payload capacity. Clark Y or E423 could be preferable if a consistent comparison shows better lift and drag characteristics for the intended flight condition.

The complete aircraft must also have adequate wing area, structural strength and thrust. Stable flight requires an appropriate centre of gravity, tail configuration and control authority.

4. Aircraft B: Manoeuvrability and Aerobatic Flight
4.1 Design requirements
Aircraft B must change direction and attitude effectively. It may experience both positive and negative angles of attack during aerobatic manoeuvres.

A symmetric airfoil is a useful candidate because its geometry is identical above and below the chord line. Its lift behaviour is approximately symmetric at positive and negative angles of attack under comparable flow conditions.

The candidates are:

NACA 0012

NACA 0015

Eppler E472

4.2 Candidate 1: NACA 0012
NACA 0012 is a symmetric airfoil with zero camber and 12% maximum thickness.

Its symmetry makes it a useful baseline for aerobatic applications because it can generate lift at both positive and negative angles of attack. Its 12% thickness may also allow a relatively thin wing section.

However, symmetry alone does not establish superior aerobatic performance. Drag, maximum lift, pitching moment, stall behaviour and the aircraft's control system must all be considered.

Assessment: A useful symmetric baseline candidate.

4.3 Candidate 2: NACA 0015
NACA 0015 is a symmetric airfoil with zero camber and 15% maximum thickness.

Compared with NACA 0012, it provides greater section thickness, which may help accommodate internal structural components. Whether this is beneficial depends on the actual wing construction.

Published aerodynamic data for NACA 0015 exists, but the exact values used in the final comparison should correspond to the chosen Reynolds number and analysis method. Values from a different Reynolds number should not be directly compared with predictions for the assumed RC aircraft.

Assessment: A reasonable preliminary candidate where symmetric lift behaviour and additional section depth are useful.

4.4 Candidate 3: Eppler E472
Eppler E472 is listed in airfoil databases and has aerodynamic data available through online airfoil-analysis resources.

It is included as an additional candidate to avoid restricting the comparison to NACA four-digit airfoils. Its suitability should be assessed using its geometry and aerodynamic polars at the same Reynolds number as NACA 0012 and NACA 0015.

A database label or intended application is not sufficient evidence that one airfoil will outperform another.

Assessment: Worth comparing, but not established as superior without matched-condition data.

4.5 Comparison of Aircraft B candidates
Criterion	NACA 0012	NACA 0015	Eppler E472
Camber	0%	0%	Must be verified from coordinates
Maximum thickness	12%	15%	Must be verified from coordinates
Symmetric geometry	Yes	Yes	Must be verified from coordinates
Positive and negative lift	Supported by symmetric geometry	Supported by symmetric geometry	Depends on actual geometry
Maximum lift coefficient at Re ≈ 203,000	Not verified here	Not verified here	Not verified here
Drag at a common lift coefficient	Not verified here	Not verified here	Not verified here
Lift-to-drag ratio at a common condition	Not verified here	Not verified here	Not verified here
Pitching moment and stall behaviour	Require matched data	Require matched data	Require matched data
Preliminary suitability	Symmetric baseline	Symmetric candidate with greater thickness	Additional candidate to evaluate
4.6 Preliminary selection for Aircraft B: NACA 0015
NACA 0015 is selected provisionally because its symmetric geometry is compatible with flight at positive and negative angles of attack, while its 15% thickness may provide useful structural depth.

This selection is based on geometry and mission reasoning, not a completed numerical ranking. NACA 0012 may be preferable if its drag and lift characteristics better suit the aircraft. E472 should also be considered after a matched-condition comparison.

Aerobatic performance depends heavily on wing loading, control-surface size, control authority, structural strength, propulsion and the aircraft's centre of gravity. The airfoil alone cannot guarantee manoeuvrability.

5. How Airfoil Geometry Influences Performance
5.1 Camber
Camber describes the curvature of the airfoil's mean line.

A cambered airfoil generally produces positive lift at zero geometric angle of attack under ordinary attached-flow conditions. This can be useful for conventional forward flight.

A symmetric airfoil has zero camber and approximately symmetric lift behaviour at positive and negative angles of attack. This is a useful starting point for aerobatic aircraft.

More camber does not automatically mean greater efficiency. It can change drag, pitching moment and stall behaviour, so the entire polar must be considered.

5.2 Thickness
Thickness affects the pressure distribution and can influence drag, separation and stall.

It also affects the available space for spars, ribs and other structural components. However, greater thickness does not automatically mean greater structural strength or better aerodynamic efficiency. Both depend on the full design.

5.3 Lift and maximum lift
The maximum lift coefficient indicates the maximum lift achievable before the airfoil's lift performance deteriorates significantly under the relevant conditions.

For an aircraft in steady flight, the approximate stall speed can be calculated as:

Stall speed = square root of [2 × aircraft weight / (air density × wing area × maximum lift coefficient)]

This relationship shows that stall speed depends on aircraft weight, wing area, air density and maximum lift coefficient. It cannot be determined from airfoil geometry alone.

5.4 Drag and aerodynamic efficiency
Drag should be compared at a relevant operating lift coefficient. The airfoil with the lowest drag at one angle of attack may not have the lowest drag at another.

Lift-to-drag ratio should therefore be compared at the same Reynolds number and comparable lift coefficients. This is especially important for small RC aircraft, where Reynolds-number effects can be substantial.

5.5 Stall behaviour
Stall occurs when flow separation prevents the airfoil from maintaining its normal lift behaviour as angle of attack increases.

Stall behaviour is affected by airfoil geometry, Reynolds number, surface roughness, turbulence and other conditions. Maximum lift and stall characteristics should be supported by appropriate data rather than inferred from thickness or camber alone.

6. Can One Airfoil Serve Both Aircraft?
One airfoil could serve both aircraft as a compromise, simplifying manufacturing and reducing the number of different wing profiles required.

However, the two missions have different priorities. The payload aircraft may prioritise useful lift and acceptable drag during conventional flight, while the aerobatic aircraft may benefit from approximately symmetric lift behaviour at positive and negative angles of attack.

For this reason, separate airfoils are provisionally recommended: NACA 4412 for Aircraft A and NACA 0015 for Aircraft B.

The decision is not absolute. If a consistent comparison shows that another profile performs better for either mission, the selection should be revised. If the same airfoil provides acceptable performance for both missions, using a common profile may be justified.

7. Factors Beyond Airfoil Selection
The following factors also influence complete-aircraft performance.

Wing area and wing loading: Wing loading is aircraft weight divided by wing area. It affects the lift required per unit area and influences stall speed.

Wing planform and aspect ratio: These influence lift distribution and induced drag.

Centre of gravity: An unsuitable position can make an aircraft unstable or difficult to control.

Tail and control surfaces: Horizontal-tail geometry, elevator authority, ailerons and rudder affect stability and manoeuvrability.

Thrust and power: The motor and propeller must provide enough thrust for the intended flight and manoeuvres.

Structural design: Spars, ribs, materials and joints must withstand aerodynamic and inertial loads.

Surface finish: Roughness, gaps and manufacturing defects can affect drag and flow separation, particularly at low Reynolds numbers.

Consequently, neither payload capacity nor aerobatic performance can be predicted from airfoil selection alone.

8. Numerical Comparison and Simulation Status
8.1 Comparison conditions
The preliminary comparison condition is Reynolds number approximately 203,000, based on an assumed airspeed of 15 m/s and mean chord of 0.20 m.

A complete numerical comparison should evaluate all six airfoils at this same Reynolds number and, where possible, use the same solver and transition assumptions.

The following values have not been filled with guessed numbers:

Parameter	Aircraft A candidates	Aircraft B candidates
Reynolds number	203,000 assumed	203,000 assumed
Maximum lift coefficient	Not yet verified at matching conditions	Not yet verified at matching conditions
Angle of attack at maximum lift	Not yet verified	Not yet verified
Drag coefficient at a common lift coefficient	Not yet verified	Not yet verified
Maximum lift-to-drag ratio	Not yet verified	Not yet verified
Pitching-moment coefficient	Not yet verified	Not yet verified
Data source and method	Requires extraction and verification	Requires extraction and verification
8.2 Recommended plots
The most useful plots for comparing the airfoils are:

Lift coefficient against angle of attack: Shows how lift changes as the airfoil rotates relative to the airflow.

Drag polar: Plots drag coefficient against lift coefficient, allowing comparison at similar lift conditions.

Lift-to-drag ratio against angle of attack: Shows the angle-of-attack region associated with high aerodynamic efficiency.

Pitching-moment coefficient against angle of attack: Useful for assessing airfoil pitching tendencies.

8.3 Simulation limitations
XFOIL is useful for estimating airfoil performance, but its predictions have limitations. Predictions can be unreliable when extensive flow separation occurs, particularly near stall or beyond stall. Very low Reynolds numbers and transition behaviour can also complicate the analysis.

Online databases may display XFOIL-derived or machine-learning predictions rather than experimental results. The method used must be identified before a numerical value is described as experimental evidence.

Simulation status: A new, matched-condition simulation for all six candidates has not been completed as part of this report. No simulation plots are claimed to have been generated.

This limitation should be resolved before claiming that the bonus simulation task has been completed. If time does not permit a simulation, the report should be submitted as a preliminary research comparison rather than misrepresenting the work.

9. Conclusion
The preliminary selections are NACA 4412 for the payload-oriented aircraft and NACA 0015 for the aerobatic aircraft.

NACA 4412 is a reasonable starting point because it has moderate camber and thickness and is supported by published aerodynamic references. NACA 0015 is a reasonable starting point because its symmetric geometry supports lift at positive and negative angles of attack, while its thickness may be useful for structural design.

Clark Y and Eppler E423 remain alternatives for Aircraft A. NACA 0012 and Eppler E472 remain alternatives for Aircraft B.

These selections are provisional because the numerical performance of all six candidates has not been compared under identical conditions. A final selection should be supported by matched-condition lift, drag, lift-to-drag ratio, pitching-moment and stall data.

The complete aircraft must also be designed with suitable wing loading, centre of gravity, control surfaces, structural strength and propulsion. The most defensible engineering decision is one that combines documented airfoil geometry, reliable aerodynamic evidence and clearly stated limitations.

10. References
University of Illinois Urbana-Champaign, UIUC Airfoil Coordinates Database. Airfoil coordinate files and related resources.
https://m-selig.web.engr.illinois.edu/ads/coord_database.html

Marchman, J. F., III, and Werme, T. D., “Clark-Y Airfoil Performance at Low Reynolds Numbers.” Wind-tunnel investigation of Clark Y at Reynolds numbers between 50,000 and 200,000.
https://stern.lab.uiowa.edu/sites/stern.lab.uiowa.edu/files/2024-11/clark-y-paper.pdf

NASA Technical Reports Server, NACA 4412 aerodynamic data. Includes experimental and calculated lift and drag comparisons at higher Reynolds numbers; these data should not be substituted directly for the assumed RC-aircraft condition.
https://ntrs.nasa.gov/api/citations/19750016605/downloads/19750016605.pdf

NASA Technical Reports Server, “Model Rotor Performance at Low Reynolds Number.” Includes NACA 0015 aerodynamic data at a Reynolds number of approximately 242,000.
https://ntrs.nasa.gov/api/citations/20205001147/downloads/Harris%20CR-20205001147_Final_7_1_2020.pdf

XFOIL Documentation, “Caveats.” Discussion of limitations in viscous airfoil analysis.
https://v0xnihili.github.io/xfoil-docs/caveats/

Foil.tools, NACA 4412 airfoil geometry and aerodynamic analysis information.
https://foil.tools/foil/naca4412

Foil.tools, Clark Y airfoil geometry and aerodynamic analysis information.
https://foil.tools/foil/clarky

Foil.tools, Eppler E423 airfoil geometry and aerodynamic analysis information.
https://foil.tools/foil/e423

BigFoil, Eppler E423 aerodynamic data resources.
https://bigfoil.com/D/7839ef81-9264-460d-b4b0-1683e7e4ab19_infoDAT.php

BigFoil, Eppler E472 aerodynamic data resources.
https://bigfoil.com/D/510b19ff-b14c-4ea4-9809-1572e947f1eb_infoDAT.php
