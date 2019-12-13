Model : North American Mesoscale (NAM) system, Global Forecast System (GFS), Short-Range Ensemble Forecast (SREF) system, High-Resolution Window (HiresW) system, Global Ensemble Forecast System (GEFS), Hurricanes in a Multi-scale Ocean Coupled Non-hydrostatic model (HMON), and Climate Forecast System (CFS)

Versions : nam.v4.1.15, gfs.v15.2.6, sref.v7.0.23, hiresw.v7.0.15, hmon.v2.1.2, cfs.v2.1.33, gsm.v12.1.6 (location of CO2 files used by GEFS)

Location of GIT tag on GitHub server:
https://github.com/RatkoVasic-NOAA/CO2_2020

Implementation Date : T.B.D.

Purpose : Run NAM to provide high-resolution mesoscale guidance to day 3.5 over North America; GFS provides short and medium-range guidance from days 1-16; SREF to provide high-resolution ensemble guidance over North America 0-87hr; HiresW to provide guidance at convective-allowing scales over the CONUS, Alaska, Hawaii, Puerto Rico, and Guam; and high-resolution hurricane guidance with HMON; GEFS provides global ensemble guidance to week 2, CFS provides monthly climate guidance. 

Developed by : EMC

Runs on WCOSS Phase 1 (CFS), Dell (GFS, NAM, SREF, GEFS), WCOSS Cray (HMON, HiresW)

Input : 
	NAM : GDAS/GFS, NAM observation files (conventional/satellite/radar data), IMS snow 	cover, RTG_SST_HR sea surface temperature analysis, Stage II/IV precipitation analyses
	SREF : GDAS/GFS/GEFS, NAM initial conditions
	HiresW : GFS, NAM and RAP for initial and boundary conditions
	GEFS : GFS
	HMON : GFS
	CFS : CFS observation files (conventional/satellite), SST/snow/sea ice analysis

Output : 
	NAM : 4x/day at 00z/06z/12z/18z; 
	SREF : 4x/day at 03z/09z/15z/21z; 
	HiresW : 00z/12z over CONUS, Hawaii, Guam, 06z/18z over Alaska and Puerto Rico; 
	GEFS : 4x/day at 00z/06z/12z/18z
	HMON : As needed by NHC at 00z/06z/12z/18z over North Atlantic and North Pacific basins
	CFS : 4x/day at 00z/06z/12z/18z

Primary Users : NWS, other NOAA agencies, private sector





Where to find output : 

On WCOSS:
	1) NAM : /gpfs/dell1/nco/ops/com/nam/prod (Dell)
	2) SREF : /gpfs/dell2/nco/ops/com/sref/prod (Dell)
	3) HiresW : /gpfs/hps/nco/ops/com/hiresw/prod (Cray)
	4) HMON : /gpfs/hps/nco/ops/com/hur/prod (Cray)
	5) GEFS : /gpfs/dell2/nco/ops/com/gens/prod (Dell)
	6) CFS : /com/cfs/prod (Phase 1)
	7) GFS: /gpfs/dell1/nco/ops/com/gfs/prod (Dell)

All systems: NCEP ftp server, NOMADS, NWS Gateway
 
1) Background / change in this release:

- Add the 2020 CO2 projection file to these system's fix directories as indicated (version numbers indicated are the new ones to account for these changes)
a) NAM (WCOSS-Dell): To /gpfs/dell1/nco/ops/nwprod/nam.v4.1.15/fix add:
nam_co2historicaldata_2020.txt
b) HIRESW (WCOSS Cray): To /gpfs/hps/nco/ops/nwprod/hiresw.v7.0.15/fix add: global_co2historical_2020.txt 
c) SREF(WCOSS-Dell): To /gpfs/dell1/nco/ops/nwprod/sref.v7.0.23/fix add: sref_co2historical_2020.txt
d) HMON(WCOSS Cray): To /gpfs/hps/nco/ops/nwprod/hmon.v2.1.2/fix/nmmb add: co2historicaldata_2020.txt 
e) GFS (WCOSS-Dell): 
i) To /gpfs/dell1/nco/ops/nwprod/gfs.v15.2.6/fix/fix_am/fix_co2_proj, add:
	global_co2historicaldata_2020.txt
ii) To /gpfs/dell1/nco/ops/nwprod/gfs.v15.2.6/fix/fix_am/fix_co2_update, add
			global_co2historicaldata_2019.txt
		iii) To /gpfs/dell1/nco/ops/nwprod/gfs.v15.2.6/fix/fix_am/co2dat_4a, add
			global_co2historicaldata_2018.txt
			global_co2historicaldata_2019.txt_proj_u
		global_co2historicaldata_2020.txt_proj
f) GEFS (WCOSS-Dell): 
	i) To /gpfs/dell1/nco/ops/nwprod/gsm.v12.1.6/fix/fix_am/fix_co2_proj, add:
		global_co2historicaldata_2020.txt 
		ii) To /gpfs/dell1/nco/ops/nwprod/gsm.v12.1.6/fix/fix_am/fix_co2_update, add
			global_co2historicaldata_2019.txt
		iii) To /gpfs/dell1/nco/ops/nwprod/gsm.v12.1.6/fix/fix_am/co2dat_4a, add
			global_co2historicaldata_2018.txt
			global_co2historicaldata_2019.txt_proj_u
			global_co2historicaldata_2020.txt_proj
	g) CFS (WCOSS Phase 1):
		i) To /nwprod/cfs.v2.1.33/fix/cfs_fix_am/fix_co2_proj, add:
			global_co2historicaldata_2020.txt
		ii) To /nwprod/cfs.v2.1.33/fix/cfs_fix_am/fix_co2_update, add
			global_co2historicaldata_2019.txt
		iii) To /nwprod/cfs.v2.1.33/fix/cfs_fix_am/co2dat_4a, add:
			global_co2historicaldata_2018.txt
			global_co2historicaldata_2019.txt_proj_u
			global_co2historicaldata_2020.txt_proj		

2) No resource changes in this release

3) Pre-implementation testing requirements: None

4) GIT tag only contains the new co2 files, so implementation instructions are as follows:
a)	In /gpfs/dell1/nco/ops/nwprod, copy entire nam.v4.1.14 . nam.v4.1.15 and copy 2020 co2 file to /gpfs/dell1/nco/ops/nwprod/nam.v4.1.15/fix
b)	In /gpfs/dell1/nco/ops/nwprod, copy entire sref.v7.0.22 . sref.v7.0.23 and copy 2020 co2 file to /gpfs/dell1/nco/ops/nwprod/sref.v7.0.23/fix (note:  the name is sref_co2historical_2020.txt)
c)	In /gpfs/hps/nco/ops/nwprod, copy entire hiresw.v7.0.14 . hiresw.v7.0.15 and copy 2020 co2 file to /gpfs/hps/nco/ops/nwprod/hiresw.v7.0.15/fix
d)	In /gpfs/hps/nco/ops/nwprod, copy entire hmon.v2.1.1 . hmon.v2.1.2 and copy 2020 
	CO2 file to /gpfs/hps/nco/ops/nwprod/hmon.v2.1.2/fix/nmmb
e)	In /nwprod, copy entire cfs.v2.1.32 .cfs.v2.1.33 and copy
	1) 2020 CO2 projection file to /nwprod/cfs.v2.1.33/fix/cfs_fix_am/fix_co2_proj
2) 2019 CO2 updated projection file to /nwprod/cfs.v2.1.33/fix/cfs_fix_am/fix_co2_update
	3) 2018-2020 CO2 files to /nwprod/cfs.v2.1.33/fix/cfs_fix_am/co2dat_4a
f)	In /gpfs/dell1/nco/ops/nwprod, copy entire gsm.v12.1.5 . gsm.v12.1.6 and copy
	1) 2020 CO2 projection file to /gpfs/dell1/nco/ops/nwprod/gsm.v12.1.6/fix/fix_am/fix_co2_proj
	2) 2019 CO2 updated projection file to  /gpfs/dell1/nco/ops/nwprod/gsm.v12.1.6/fix/fix_am/fix_co2_update
	3) 2018-2020 CO2 files to /gpfs/dell1/nco/ops/nwprod/gsm.v12.1.6/fix/fix_am/co2dat_4a
      g)  In /gpfs/dell1/nco/ops/nwprod, copy entire gfs.v15.2.5 . gfs.v15.2.6 and copy
	1) 2020 CO2 projection file to 	/gpfs/dell1/nco/ops/nwprod/gfs.v15.2.6/fix/fix_am/fix_co2_proj/
	2) 2019 CO2 updated projection file to  	/gpfs/dell1/nco/ops/nwprod/gfs.v15.2.6/fix/fix_am/fix_co2_update
	3) 2018-2020 CO2 files to /gpfs/dell1/nco/ops/nwprod/gfs.v15.2.6/fix/fix_am/co2dat_4a
