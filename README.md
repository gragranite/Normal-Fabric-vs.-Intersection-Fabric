# Normal-Fabric-vs.-Intersection-Fabric
Ver. 1.0
© 2025 Takato Takemura, Geomechanics Lab., Nihon University


This tool is an interactive HTML application to visualize and compare the normal fabric tensor (N_ij) and the intersection fabric tensor (C_ij) of a disk-shaped fracture (crack) set. It generates unit normal vectors, computes their second-rank fabric tensors, and plots the principal directions on a lower-hemisphere equal-angle stereonet. It also shows a simple model of the intersection length distribution.

You can open the HTML file directly in a web browser (no server or installation required).
1. Features
•	Random generation of disk normals in 3D: uniform on the unit sphere or concentrated around the x, y, and z axes with a user-controlled ratio and concentration.
•	Computation of the normal fabric tensor N_ij = <n_i n_j> and the intersection fabric tensor C_ij = <c_i c_j>.
•	Eigenvalue and eigenvector analysis of N_ij and C_ij (principal values λ1, λ2, λ3 and principal directions).
•	Stereonet plot (lower-hemisphere, equal-angle projection) showing poles of disk normals and principal axes of N_ij (blue symbols) and C_ij (red symbols).
•	Simple Monte Carlo model for intersection length between overlapping disks, including histogram and basic statistics (mean, standard deviation, quantiles).
•	SVG export: download the stereonet as an SVG file with one click.
2. How to Open the App
1. Save the HTML file (e.g., stereonet_principal_symbols.html).
2. Double-click the file or open it with a modern web browser (Chrome, Firefox, Edge, Safari).

All computations run locally in the browser via JavaScript. No installation or internet connection is required.
3. Input Panel
All input controls are on the left side under “Input”. The key parameters are summarized below.
3.1 Number of disks (normals) N
Label: Number of disks (normals) N
Default: 100
This is the number of disk normals generated on the unit sphere. Each normal vector n represents the orientation of a disk (fracture).
3.2 Generation pattern
Label: Generation pattern
Options:
  • Random (uniform on sphere): normals are sampled uniformly on the unit sphere.
  • Concentrated around x, y, z: normals are sampled as clusters around the x, y, and z axes.
3.3 x:y:z ratio (for axis_mix)
Label: x:y:z ratio (for axis_mix)
Default: 1:1:1
Only used when the generation pattern is “Concentrated around x, y, z”. This ratio controls the relative number of normals clustered around the x, y, and z axes. For example, 1:1:1 gives an isotropic mixture of three axial clusters, while 2:1:1 produces more normals around the x-axis.
3.4 Degree of concentration (σ, deg)
Label: Degree of concentration (σ, deg)
Default: 15 (degrees)
Standard deviation (in degrees) of the angular spread around each axis for the axis_mix pattern. Smaller σ means stronger concentration (tighter clusters), while larger σ produces broader distributions.
3.5 Disk diameter (2r, units)
Label: Disk diameter (2r, units)
Default: 2
Diameter 2r of each disk (arbitrary units). This parameter is used in the intersection length model (not in the stereonet geometry itself).
3.6 Number of sampled intersection pairs M
Label: Number of sampled intersection pairs M
Default: 50000
Number of Monte Carlo samples used to generate the approximate distribution of intersection lengths. Larger values give smoother histograms but require more computation time.
3.7 Random seed
Label: Random seed
Default: 0
Integer seed for the pseudo-random number generator. Using the same seed reproduces the same set of disk normals, principal axes, and intersection-length distribution.
3.8 Show principal axes of C_ij
Checkbox: Also show principal axes of intersection tensor C_ij
If checked, the principal axes of C_ij are plotted on the stereonet (red symbols). If unchecked, only the principal axes of N_ij are displayed.
4. Buttons
4.1 Generate
Button: Generate
Generates disk normals according to the current input settings, computes N_ij and C_ij, performs eigenvalue analysis, updates the stereonet figure, and redraws the intersection-length histogram and statistics table.
4.2 Download stereonet SVG
Button: Download stereonet SVG
Exports the current stereonet as an SVG file. The filename includes a timestamp. The exported SVG contains the outer circle, the poles of disk normals, and the principal axes symbols of N_ij and (optionally) C_ij.
5. Output Panels
5.1 Summary
The Summary box displays:
  • N: number of generated disk normals.
  • number of intersection pairs: the number of unique normal pairs used in the calculation of C_ij.
  • tr(N): trace of the normal fabric tensor N_ij (should be close to 1 for a normalized second-order tensor).
  • tr(C): trace of the intersection fabric tensor C_ij (if defined; otherwise shown as “—”).
5.2 Stereonet plot
The stereonet shows a lower-hemisphere equal-angle projection:
  • Gray dots: poles of disk normals.
  • Blue symbols: principal axes of N_ij (circle, triangle, square for λ1, λ2, λ3, respectively).
  • Red symbols: principal axes of C_ij (circle, triangle, square for λ1, λ2, λ3, respectively; shown only if enabled).
The symbol sizes are scaled qualitatively with the eigenvalues to emphasize anisotropy.
5.3 Fabric tensors and eigenvalues
Below the stereonet, two sets of tables are shown side by side:
  • Left: normal fabric tensor N_ij.
  • Right: intersection fabric tensor C_ij.

For each tensor, the following tables are displayed:
  • Full 3×3 matrix in the xyz-coordinate system.
  • Eigenvalues and eigenvectors (principal values λ1, λ2, λ3 and their directions).
  • Diagonalized matrix with eigenvalues on the diagonal.

5.4 Intersection-length histogram and statistics
The bottom panel displays a histogram of the approximate intersection lengths between overlapping disks. The model assumes:
  • Each disk has chord length L = 2*sqrt(r^2 − s^2), where s is uniformly distributed.
  • The relative shift between two chords is also assumed uniform.

The right-hand table lists basic statistics (mean, standard deviation, min–max) and selected quantiles (p10, p25, p50, p75, p90, p95, p99).
6. Notes and Limitations
•	The stereonet and tensors are based on unit normal vectors only; no spatial information about disk positions is included.
•	The intersection fabric tensor C_ij is computed from cross products of pairs of normal vectors. If most normals are nearly parallel, C_ij may be poorly defined or unavailable.
•	The intersection-length model is a simplified Monte Carlo approximation and is not a full 3D discrete fracture network simulation.
•	All computations are performed in JavaScript within the browser. Results may differ slightly between browsers due to floating-point implementations.
