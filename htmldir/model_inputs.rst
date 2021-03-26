============
Model Inputs
============

Synthetic Population
--------------------

Land Use Inputs
---------------
Traffic Analysis Zone (TAZ) Data
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Tables 
~~~~~~~

`TABLES <http://intranet2.sfcta.org/Modeling/TAZDataProcessor#Employment_Categories>`_ — the following four categories are found in this section:  

*	Table 1: SIC-based Employment Categories in MTC Data Inputs  

*	Table 2: Employment Categories in SF Data Inputs, Available only for SF County  

*	Table 3: NAICS-Based Employment Categories in MTC Data Inputs  

*	Table 4: Correspondence between MTC-NAICS and SF Employment Categories  

*	Table 5: Formulas to Convert MTC-NAICS to SF Employment Categories  


Employment Categories
~~~~~~~~~~~~~~~~~~~~~
  
The most prominent difference in data inputs is in the definition of the employment categories inside and outside of San Francisco. For non San Francisco TAZs, the CHAMP model system used employment information from the MTC model’s master zonal data file (ZMAST), which is grouped in the six categories shown in Table 1. The data are available for all TAZs in the Bay Area and are based on the ABAG Projections series. For San Francisco TAZs, CHAMP used a differentset of employment groupings, shown in Table 2, that are provided by the San Francisco Planning Department and only available for San Francisco County. Both sets of employment classifications are primarily defined by the Standard Industrial Classification (SIC) codes, though the Planning Department scheme also reflects location information in addition to business sector information. 


Versions of the ZMAST based on Projections 2005 and later include a second set of employment categories based on the North American Industrial Classification system (NAICS), the successor to SIC. Table 3 shows these categories and Table 4 shows the approximate correspondence to the San Francisco groups. These new employment categories are a step closer to the San Francisco categories than the SIC categories are. Specifically:

*	Production, Distribution & Repair only requires the aggregation of two categories (Manufacturing, Wholesale Trade & Transportation + Agriculture & Natural Resources).  

*	A Financial & Professional Services category is provided, which roughly corresponds to the SF Management, Information & Professional Services category.  

*	A Health, Recreation & Educational Services category is provided, which only needs to be disaggregated into two categories.  
  
In summary, the Planning Department employment categories attempt to provide information more relevant to the characteristics of San Francisco. Unfortunately, the additional relevance comes at a cost of inconsistency with the remainder of the Bay Area. An approach wasdeveloped to resolve these inconsistencies, as described below.  

Table 5 summarizes the approach used to calculate employment in each of the SF employment categories for zones outside San Francisco. In most cases, the employment totals are calculated as combinations of NAICS and/or SIC categories available in the MTC ZMAST file. Unfortunately, the categories do not always line up cleanly. For example, the NAICS OTHEMPN category includes Construction employment, which is counted in PDR, as well asInformation and Public Administration which are counted in MIPS. Given no specific knowledge of which zones contain Construction employment, and which contain Information or Public Administration employment, all are assumed to be distributed evenly, and the total is split up using the regional share of each. A similar approach is taken to derive the VISITOR and CIE employment from a larger total.  
  
Another item of note is that the NAICS definition of retail employment differs from the SIC definition of retail employment in that it does not include Eating & Drinking Places. For consistency with the SF definition, the SIC definition is used outside San Francisco. Similarly, the Eating & Drinking Places must be subtracted out from the Health, Education, and Recreation Services employment to derive VISITOR and CIE employment.  

A similar aggregate approach for locating MED employment was rejected because medical centers, particularly hospitals tend to be highly concentrated employment centers that attract a lot of trips. Since such a high concentration of trips is involved, it is important to get their locationscorrect. To do this, disaggregate employment information was obtained from MTC and used to determine the amount of base-year medical employment in each TAZ. This was related to the total Health, Education and Recreation Services employment in the TAZ to calculate a share ofmedical for each. This share is held constant over time, and if the total increases, then the medical employment will also increase.  

Within San Francisco, the existing employment data are used. The conversion factors described above only apply to the outlying counties.



Micro Analysis Zone (MAZ) Data
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Network Inputs
--------------
Highway Network
^^^^^^^^^^^^^^^
Transit Network
^^^^^^^^^^^^^^^
Fares & Pricing
~~~~~~~~~~~~~~~

IXXI Demand
-----------
