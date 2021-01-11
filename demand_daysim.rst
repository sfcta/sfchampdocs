----------------------------------
DaySim Activity-Based Demand Model
----------------------------------

SF-CHAMP 6.0 uses the DaySim demand model (https://github.com/RSGInc/DaySim/wiki). DaySim is an open-source travel demand microsimulation package that is used by several regional planning organizations in their travel demand models. DaySim consists of a series of discrete choice models that represents different components of travel decision-making. Each model is estimated and calibrated with observed travel survey data.
This is an abridged list of DaySim submodels and some of the primary factors that influence choice-making in each model, roughly presented in order:
*	Work location model
  *	Major sensitivities include: full or part-time status, distance, income, sex, and quantity of jobs by industry sector
*	School location model	
  *	Major sensitivities include: student age, distance, and school enrollment in base year by school level
*	Auto ownership
  *	Major sensitivities include: number of drivers in household, numbers of household members of various status (child, student, worker, retired, etc.), household income, commute/school logsum benefit of car ownership (how much would car ownership improve work commute or school accessibility), distance to transit stops, parking prices near home, amount of food, retail, service, and medical employment near home
*	Person day pattern
  *	Major sensitivities include: worker/student status, income, auto ownership, sex, age, activity purpose, land use attributes, family composition (e.g. has children in household)
*	Tour destination models (work, other, subtour)
  *	Major sensitivities include: full-time worker status, part-time worker status, student status, employment density, is/is not usual workplace, distance, activity purpose, day pattern, home/non-home based, income, auto availability, other land use attributes
*	Tour mode models (work, school, work-based, escort, other home based)
  *	Major sensitivities include: travel time, transit fares, tolls, parking cost, income, age, sex, auto ownership, household size, children in household, origin and destination land use attributes, stops in tour pattern by activity purpose
*	Tour time models (work, school, other work-based)
  *	Major sensitivities include: tour mode, activity purpose, day pattern (other tours in day, tour order, etc.), worker and student status, income
*	Intermediate stop generation model
  *	Major sensitivities include: tour purpose, number of tours in day pattern,  time of day, duration of tour time window, sex, age, household type, tour mode, worker status, children in household status, position of stop within tour
*	Intermediate stop location model
  *	Major sensitivities include: stop activity purpose, travel time available, distance, income, tour purpose, tour mode, land use attributes (employment density, etc.), 
*	Trip mode model
  *	Major sensitivities include: tour mode, activity purpose, travel time, transit fares, tolls, parking cost, auto ownership, household size, household composition (children in household), land use density, intersection density, age, income
*	Trip time model
  *	Major sensitivities include: student status, age, minutes available in schedule, remaining stops to make, activity purpose
