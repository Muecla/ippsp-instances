# ippsp-instances
Generated instances for the integrated project and personnel scheduling problem (IPPSP)

## Problem description
The IPPSP consists of several projects that have preemptive and multi-modal activities that need to be completed before given deadline.
The activities require resources, which are personnel and equipment. The personnel is a heterogeneous workforce that includes people with different subsets of skills, while each of the pieces of equipment is designated a type.
Equipment needs to be transported between the different locations. To ensure that it is possible to undertake activities even though there is not enough personnel or equipment, it is possible to rent external resources to a higher price.

## Instance documentation
The instances that can be found in the [instances](instances) folder are defined using the format used by FICO Xpress Mosel.

The instance parameters are listed and explained below.

### Scalar parameters
For parameters that are scalars, there are only one number and no brackets after the colon.

#### Scalars included
- **nEmployees**
- **nSkills**
- **nProjects**
- **nDays** 
- **nActivities**
- **nEquipmentTypes**
- **nStints** 
- **nMaxModes**: number of modes for the activity with the most modes
- **nStintCliques**: the number of maximal stint cliques

### One-indexed parameters
- **OverlappingStints**: The indices are stints, and each value is a set of overlapping stints
- **EmployeesWithSkill**: The indices are skills, and each value is a set of employees
- **EmployeesThatShouldNotWorkTogetherWithEmployee**: The indices are employees, and each value is a set of employees
- **ImmediatePredecessorsToActivity**: The indices are activities, and each value is a set of activities
- **ActivitiesInProject**: The indices are projects, and each value is a set of activities
- **nActivityModes**: The indices are activities, and each value is an integer
- **StintsInProject**: The indices are projects, and each value is a set of stints
- **WorkingStintsOnDay**: The indices are days, and each value is a set of stints
- **ProjectStart**: The indices are projects, and each value is an integer
- **ProjectEnd**: The indices are projects, and each value is an integer
- **EarliestStartDayForActivity**: The indices are activities, and each value is an integer
- **LatestStartDayForActivity**: The indices are activities, and each value is an integer
- **MaximalStintCliques**: The indices are stint cliques, and each value is a set of stints

### Two-indexed parameters
These parameters are accessed using two integers. Some of the two-indexed parameters are given as sparse matrices.
Sparse matrices are provided with the indices in parentheses and the corresponding value is immediately succeeding, e.g., _(1 4) 1000_.

#### Two-indexed parameters included
- **EmployeeInStintCost**: The indices are (employee, stint) tuples, and each value is an integer
- **ExternalWorkerWithSkillOnStintCost**: The indices are (skill, stint) tuples, and each value is an integer
- **EmployeeAvailability**: The indices are (employee, stint) tuples, and each value is binary (1 if available, 0 otherwise)
- **EmployeeWantedInStint** (sparse matrix): The indices are (employee, stint) tuples, and each value is 1 if present (assume 0 if not present) 
- **EmployeeWantedViolationCost** (sparse matrix): The indices are (employee, stint) tuples, and each value is an integer (assume 0 if not present)
- **ShouldNotWorkTogetherCost** (sparse matrix): The indices are (employee, employee) tuples, and each value is an integer (assume 0 if not present)
- **ActivityDurationWithMode**: The indices are (activity, mode) tuple, and each value is an integer
- **ExternalEquipmentRentingCost**: The indices are (activity, equipment type) tuples, and each value is an integer
- **TotalNumberOfInitialEquipmentTypeLocation** (sparse matrix): The indices are (equipment type, depot activity) tuples, and each value is an integer (assume 0 if not present)

### Three-indexed parameters

- **SkillDemandInActivityWithMode**: The indices are (skill, activity, mode) tuples, and each value is an integer
- **EquipmentTypeDemandInActivityWithMode**: The indices are (equipment type, activity, mode) tuples, and each value is an integer
- **EquipmentTypeTransportationCost**: The indices are (project, project, equipment type) tuples, and each value is an integer
- **TransportationTimeForEquipmentTypeBetweenProjects**: The indices are (project, project, equipment type) tuples, and each value is an integer

### Sets
- **DepotActivities**: Includes the subset of activities that are depot activities