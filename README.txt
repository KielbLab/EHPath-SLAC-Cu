This repository contains a modified version of the original EHPath (Electron-Hole Pathways) code developed by Teo et al. The modification extends the original code to include copper (Cu) as a possible initial hole donor.

The modified code was used to investigate hole-hopping pathways in the small laccase (SLAC) from Streptomyces coelicolor. The repository includes the modified Python script, the input files used for the calculations and the complete terminal output.



--------------------Original code and attribution--------------------

The original EHPath code was developed by Teo et al. and is available at:
https://github.com/etransfer/EHPath
Original Publication:
Teo, R. D.; Wang, R.; Smithwick, E. R.; Migliore, A.; Therien, M. J.; Beratan, D. N. "Mapping hole hopping escape routes in proteins." Proc. Natl. Acad. Sci. U.S.A. 2019, 116.32, 15811–15816.

https://doi.org/10.1073/pnas.1906394116

The original code is copyrighted by its original authors:

Copyright (C) 2019 Teo, R. D.; Wang, R.; Smithwick, E. R.; Migliore, A.; Therien, M. J.; Beratan, D. N.

The modifications described below are based on this original implementation.



--------------------Modifications to the original code--------------------

The code was modified by Müller-Pilz, F.H. in 2026 as part of the research presented in:

Scharbach, C., Müller-Pilz, F.H., Ciaccafava, A., Gräve, C., Kielb, P., "Systematic disruption of Tyr/Trp pathways amplifies the ROS formation 25-fold in multicopper oxidase", under revision

The modifications introduce copper as a possible initial hole donor while retaining the original EHPath framework for calculating and ranking electron/hole hopping pathways.

The following changes were made to the original EHPath.py script:

1) Added Cu (CU) to the node class, with the following parameters:
	- Lamb = 1.378
	- E = 1.1
	- r = 1
2. Extended the smallK() function to include copper as a possible hole donor for the following hole transfer steps:
- Forward transfer from Cu to amino acid bridge
- Backward transfer from amino acid bridge to the initial Cu donor
- Direct hole transfer from Cu to a terminal amino acid acceptor

For these calculations, the existing heme-based expressions for the reorganization energy and electronic coupling are retained, while the Cu-specific parameters defined in the node class are used.

The remaining calculations and functionalities of the original EHPath script are unchanged.

--------------------Repository contents--------------------

The repository contains the following files:

EHPath_modified/
│
├── EHPath_modified.py
├── README.md
├── LICENSE
│
├── inputs/
│   ├── donor_3cg8.csv
│   ├── bridge_3cg8.csv
│   └── acceptor_3cg8.csv
│
└── output/
    └── terminal_output_3cg8.txt

EHPath_modified.py: Modified version of the original EHPath script, including Cu as a possible initial hole donor.

inputs/: Input files defining the donor, bridging sites and acceptor sites used in the SLAC calculations.

output/terminal_output_3cg8.txt: Complete terminal output from the calculation using the supplied input files and parameters.

LICENSE: GNU General Public License, version 3.


--------------------Structural input--------------------

The input files were generated from the crystal structure of the small laccase (SLAC) from Streptomyces coelicolor.

Protein Data Bank entry: 3CG8

The donor, bridge and acceptor files supplied in the inputs/ directory were used for the calculations reported in
Scharbach, C., Müller-Pilz, F.H., Ciaccafava, A., Gräve, C., Kielb, P., "Systematic disruption of Tyr/Trp pathways amplifies the ROS formation 25-fold in multicopper oxidase", under revision



--------------------Requirements--------------------

The script requires Python and the following packages:

NumPy
pandas
NetworkX

Install the required packages using:

python -m pip install numpy pandas networkx



--------------------Reproducing the calculations--------------------

Download the repository and open a terminal in its root directory, i.e., the directory containing EHPath_modified.py.

Run the following command:

python EHPath_modified.py

The script will ask for the input files and calculation parameters.

To reproduce the calculations using the supplied SLAC input files, enter the following values when prompted:

Please enter the name of donor file (eg: donor.csv): inputs/donor_3cg8.csv
Please enter the name of bridge file, (eg: bridge.csv): inputs/bridge_3cg8.csv
Please enter the name of acceptor file, (eg: acceptor.csv): inputs/acceptor_3cg8.csv
Please enter residue number of donor: 1414
Please enter cutoff_num (cutoff_num + 1 = maximum number of nodes in the pathway, Warning: A larger cutoff_num will cost more memory and leads to longer computation time): 5
Please specify the number of pathways to be printed: 400
Please enter the type of donor/acceptor (electron or hole): hole
Please specify the value for α: 1

The calculation starts after the final input has been entered.

The complete terminal output obtained using these settings is provided in output/terminal_output_3cg8.txt.



--------------------Citation--------------------

If you use the modified code in your research, please cite the original EHPath publication and the publication describing the modifications.

Original EHPath publication:

Teo, R. D.; Wang, R.; Smithwick, E. R.; Migliore, A.; Therien, M. J.; Beratan, D. N. "Mapping hole hopping escape routes in proteins." Proc. Natl. Acad. Sci. U.S.A. 2019, 116, 15811–15816.

https://doi.org/10.1073/pnas.1906394116

Publication describing the modified code and its application:

Scharbach, C., Müller-Pilz, F.H., Ciaccafava, A., Gräve, C., Kielb, P., "Systematic disruption of Tyr/Trp pathways amplifies the ROS formation 25-fold in multicopper oxidase", under revision



--------------------License--------------------

The original EHPath code is copyrighted by its original authors and is distributed under the GNU General Public License, version 3 (GPL-3.0).

This modified version is distributed under the same license. The original copyright and license notices are retained, and the modifications are identified separately.

The full license text is provided in the LICENSE file.

This software is provided without warranty, as specified in the GNU General Public License.