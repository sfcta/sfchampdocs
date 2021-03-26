=======================
User Guide
=======================

---------------------
Running a Model
---------------------

Preparing Inputs
^^^^^^^^^^^^^^^^^

Land Use Coding
~~~~~~~~~~~~~~~~~~

See `Land Use Projections <http://intranet2.sfcta.org/Modeling/LandUseProjections>`_ for documentation on the current set of land use projections we use.  
  
See `Disaggregate Input Output Key <http://intranet2.sfcta.org/Modeling/DisaggregateInputOutputKey#TAZDATA_dbf>`_  for the fields in the land use input file, tazdata.dbf.

TAZ Data Processor
~~~~~~~~~~~~~~~~~~

See `TAZ Data Processor <http://intranet2.sfcta.org/Modeling/TAZDataProcessor>`_ for information about the TAZ Data Processor. Trivial modifications were made to the process for CHAMP 4.3 Fury (Noted in TAZDataProcessor).


Population Synthesizer
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

See `Population Synthesizer <http://intranet2.sfcta.org/Modeling/PopulationSynthesizer>`_ for information about the Population Synthesizer.No modifications were made to the code or configuration for CHAMP 4.3 Fury.

Network Coding
~~~~~~~~~~~~~~~~

See `Network Coding Guidelines <http://intranet2.sfcta.org/Modeling/NetworkCodingGuidelines>`_ for general network coding (this page is fairly lacking in content and should be deprecated?).  

See `Network Wrangler <http://intranet2.sfcta.org/Modeling/NetworkWrangler>`_ for more information about the tool we use to build networks from a set of projects.  

Run Setup
^^^^^^^^^^^^^^

Including `Setup New Model Run <http://intranet2.sfcta.org/Modeling/SetupNewModelRun>`_.

Troubleshooting
^^^^^^^^^^^^^^^^^^^

If a model run crashes, first step is to look at the DOS window and see what it told you and also check feedback.rpt in the run directory, which also gives you a hint about what is going on, what ran correctly, what isn't working correctly. Another good clue often comes from looking at the run directory or the current transit assignment subdirectory, sorted by time.  
  
*	The first thing to check is whether we've run out of space on the X: drive… (really this is something to check before starting a model, but we all forget sometimes.)   

*	If a Cube script fails (return code 2), then find the appropriate print log files by sorting the run directory by time, and looking for F(, which signifies where the failure in cube occurs.  

*	Sometimes a cube script will fail because a previous step in the model chain didn't work out correct. For example, if the step for averaging trip tables doesn't work, this is usually because one or all of the model cores failed to run, so the appropriate input files weren't there to average.  

*	The walk skims part of pre-processing can be a little bit fragile, especially whenever it needs to use arcpy. TARAVAL needs to have a GIS license for this step; we usually keep an ArcMap window open to make sure it can get one, but check if this has been closed. If arcpy complains about trying to add a field which already exists (e.g. gislen) that probably means it's trying to run the same script twice -- either you can skip ahead to the completion of that script or you need to roll back to earlier in the model run and undo the addition of those fields (if you need the original FREEFLOW.NET, it's in inputs\hwy). If arcpy complains about the ``VALUETOLL_`` field, the most likely problem is an out-of-date version of the TI_Ramps project -- the current version of that project excludes that field.  

*	Occasionally the highway network gets built with some field errors that cause model crashes. Check that all links have MTYPE set to either SF or MTC and that all links have distance>0.  

*	If the core has failed, check to make sure there was enough space locally on the core machine (i.e. MINNA or ZOE or BONECRUSHER) to write the outputs and also check that the X-drive wasn't full. This is also often accompanied by a pop-up "delay write failure".  

*	Another possible reason the core could have failed was that it couldn't find the machine it was supposed to send the core to (i.e. "calling BONECRUSHER, couldn't find BONECRUSHER"). There are two possible reasons for this: (1) bonecrusher has shut itself down. you can test this by trying to VNC or ping bonecrusher; (2) the champ client isn't running on bonecrusher, or it is running with an incompatible version of Python. Check bonecrusher to see if the correct champ client is running. We also have sometimes had problems with dispatching to a champ client because of the Windows firewall -- if a modeling machine is new or has recently been upgraded, that's a good thing to double-check.  

*	Occasionally we've had trouble importing Wrangler, specifically the transitAssignmentData module. Sometimes this can be solved by deleting the .pyc files (the compiled python scripts); sometimes this has actually masked other issues because Wrangler automatically tries both transitAssignmentData and TransitAssignmentData, and isn't currently setup to report why one fails if it tries the other.  

*	In Cube 5, we had a lot of trouble with crashes during transit assignment and skimming. I think (cross fingers) that's mostly solved in Cube 6, but in case it's not, here's a bit about what tended to happen and how to fix it. Sometimes one of the cluster nodes would either not respond, or would be skipped over, causing the master process to keep waiting for a non-existent process to finish -- classic symptom is a "waiting for files to be created" window with all but one box checked, that lasts for more than 5 or 10 minutes. To re-start, you want to make sure to run every script that hasn't already run, but not run the ones which have -- check for which output files have been created, then edit the trnAssign.jset or trnSkim.jset file to remove the scripts that have already run and restart the model with goto statements directing it to start with that jset. Sometimes you can be clever and restart one of these without actually stopping the main model process -- if the model has hung waiting for CHAMP4.script.end, you can just run the CHAMP4.script from the command line and create the .script.end file which just contains the return code (hopefully 1) and the name of the PRN file. Once the .script.end file has been created, the master process will recongnize it and resume working.  

*	The bike model sometimes hangs on bike assignment or (less commonly) bike logsums. As far as I can tell, the issue is somewhere in python's multiprocessing package, and what seems to happen is that the subprocesses all finish but the message doesn't get back to the main process. I'm not sure what the solution is to this one.
