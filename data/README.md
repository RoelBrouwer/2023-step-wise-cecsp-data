# File format definition for instances
Instances can be stored in binary (NumPy) or CSV format. The latter is easily explored manually and will be defined below.

An instance, when stored in .csv-format, comprises four files:
- `constants.csv` contains a semicolon-separated list of constants and their labels associated with the instance.  
  These instances only have a single constant defined, namely `resource_availability` $P$. An example constants-file might look as follows:  
  ```
  resource_availability;25.0
  ```
- `jumppoints.csv` contains a row (or line) for every job, listing all relevant times associated with a job in a semicolon-separated list. The first element is its release date $r_j$ and the last its deadline $\bar{d}_j$. In between are the k-1 jump points listed in order. The first row contains the data for the job with index 0, the second for job with index 1 and so on.  
  An example jumppoints-file (for five jobs and two jump points) might look as follows:
  ```
  0.52;6.24;7.41;8.02
  0.94;4.66;9.06;13.01
  0.00;6.11;9.56;11.91
  4.07;10.17;10.18;15.56
  4.80;7.07;8.48;10.66
  ```
- `properties.csv` contains a row (or line) for every job, listing its associated properties in a semicolon-separated list. The first row contains the data for the job with index 0, the second for job with index 1 and so on.
  An example properties-file (for five jobs) might look as follows:
  ```
  12.83;0.32;4.70
  79.00;8.31;22.07
  83.87;0.00;27.48
  75.05;6.92;33.74
  67.64;0.10;35.06
  ```
  The properties listed are, in order:
    - resource requirement $E_j$;
    - resource lower bound $P^-_j$;
    - resource upper bound $P^+_j$.  
- `weights.csv` contains a row (or line) for every job, listing the cost of completing the job in an interval in a semicolon-separated list. The first element is its base cost, with each subsequent value being the increment added for completing the job during or after each interval. The first interval runs from the release date $r_j$ to the first jump point, and so on, following the intervals defined by the value in `jumppoints.csv`. The first row contains the data for the job with index 0, the second for job with index 1 and so on.  
  An example weights-file (for five jobs and two jump points) might look as follows:
  ```
  2.45;1.70;0.74
  4.81;0.05;0.03
  4.82;0.02;0.11
  0.95;0.09;1.44
  2.24;0.41;0.76
  ```
