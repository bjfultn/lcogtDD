lcogtDD
---------

Want to download data automatically from LCOGT? This is the python code to do it. 

For quick usage, fill in your user data under `userdata.dat` and run the code 
by doing:

        python download_data.py -sdate 2016-04-01 -edate 2016-04-21

And that's it! Reduced data taken from LCOGT between 2016-04-01 and 2016-04-21 will be 
downloaded to your computer. If you only give a starting date with `-sdate`, then data 
will be downloaded from this date to the current date on your computer (i.e., "today"). 
See below for a detailed explaination on the usage of the code.

Dependencies
------------

The code needs the following libraries to be installed in order to work:

    - numpy (http://www.numpy.org/).
    - requests (http://docs.python-requests.org/en/master/).

Usage
-----

To use the code is simple: 

1. Fill in your LCOGT archive username, password, data folder and the name of 
   the proposals (separated by commas if there are more than one) for which you want 
   to check data on the `userdata.dat` file (the `datafolder` variable which you have 
   to fill is the data folder under which you want to download the LCOGT data. If you 
   already have LCOGT data, this folder should contain a folder called `raw` and, 
   inside, the frames ordered in sub-folders with the dates of these frames as names. 
   For example, if `datafolder = myfolder`, then the data for `20160416` is expected to be under
   `myfolder/raw/20160416/`). 

2. Select the dates between which you want to check data. If, for example, you want to 
   download reduced data from LCOGT between 2016-04-01 and 2016-04-21, then simply do:

               python download_data.py -sdate 2016-04-01 -edate 2016-04-21
   
   The only required input here is the starting date; if the ending date is not given, it 
   will be assumed you want all the data from the starting date to the current date, where 
   "current date" is the current date in your computer. In other words, running :

               python download_data.py -sdate 2016-04-01

   will download all the data from 2016-04-01 to the current day.

3. Optional: you can also add the proposal IDs in command line. To fetch data from proposals 
   MyProp-001 and MyProp-002, for example, you can do:

       python download_data.py -sdate 2016-04-01 -proposalID "MyProp-001,MyProp-002"

   Note this will override the userdata.dat proposals, in order to preserve back-compatibility.

4. Optional: you can also add the data folder in which the data will be stored. If you want to 
   store the data of proposal MyProp-001 in "/home/myuser/myLCOGTdata", just do:

       python download_data.py -sdate 2016-04-01 -proposalID "MyProp-001" --datafolder "/home/myuser/myLCOGTdata"

   Note this will override the datafolder in userdata.dat, in order to preserve back-compatibility.

Note that the code checks if a given frame is already downloaded. If it is on the system, then 
the frame is not downloaded.
