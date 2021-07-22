# Scripts
To process the raw TotTag files for this project, the following scripts were used. 
*Note, updated preprocessing scripts have been developed since publication of this project. See https://github.com/lab11/socitrack/tree/master/software/analysis for the most up to date TotTag analysis methods.

To begin, first run the tottagAverager.py script, which takes at least 3 arguments: the starting Unix timestamp, the ending Unix timestamp, and a list of every log file that you would like to average together. The data is averaged accross timestamps by dyad, so the measured value at a certain timestamp from one TotTag is averaged with the value at the same timestamp from its companion TotTag. The script can be run like so:

python tottagAverager.py START_TIME_VAL END_TIME_VAL LOG_FILE_1 LOG_FILE_2...

Next, run the tottagSmoother.py script, which takes at least 2 arguments: the number of data points over which to smooth, followed by a list of every log file you would like to smooth. The smoother works by taking a moving average with a width of SMOOTHING_VAL [3 for this project]. When it encounters a gap in the data greater than the aforementioned value, the smoothing buffer is cleared and it starts over after the gap. To run the script, enter:

python tottageSmoother.py SMOOTHING_VAL AVERAGED_LOG_FILE_1 AVERAGED_LOG_FILE_2...