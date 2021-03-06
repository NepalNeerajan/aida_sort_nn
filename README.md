AIDA sort code v1, May 20th 2017


Contents:
config: folder with configuration files (e.g. calibration parameters)
files: [not used in current version]
include: C++ header files	
src: C++ source code with implementation of sort functions
main.cpp: main code to control execution of sort algorithm  
Makefile: make file to compile code  
README: this!  




- To compile:
> make

Will produce 'aida_sort_nn_v1.exe' executable file

- For help menu:
> ./aida_sort_nn_v1.exe -h

Dsiplays options to run code:

	-O (for online data analysis, source_option=2)
	-i [id=0] (DataSpy id for online data)
	-F [RunName] (for data analysis from file, source_option=1)
	-d [DataDir] (directory path for data file)
	-x (enable data Xfer to remote DataSink, options in ./config directory)
	-U [unpacker_option=0] (Unpacker output level; 0: no ouput, 1: histograms, 2: TTree, 3: histograms+TTree)
	-C [calibrator_option=1] (Calibrator output level; 0: no ouput, 1: histograms, 2: TTree, 3: histograms+TTree)
	-A [analysis_option=1] (Analysis output level; 0: no ouput, 1: histograms, 2: TTree, 3: histograms+TTree)
	-w [time_window=3202] (time_window for event clustering)
	-R (enable writing output to Root file)
	-L [RLrun=-1, RLfirst, RLnum] (loop over list of MIDAS data files, overrides option -F if RLrun>0)
	-v (verbose mode)




- As an example, the following line:

>./aida_sort_nn_v1.exe -F Run000 -U 0 -C 1 -A 3 -R

will run the code for the data file Run000. It will produce, and save to file, the default histograms for the Calibration step ('-C 1'), and the histograms and TTree with sorted data for the Analysis step ('-A 3'). The analysis step includes the event reconstruction algorithm.

The option '-R' is important to open the Root output file ('aida_sort_Run000.root', naming is automatic), otherwise the output will not be saved once code finishes execution.

>./aida_sort_nn_v1.exe -L 25 24 13 -U 2 -C 2 -A 2 -R

will run the code for the data file's from R25_24 to R25_36 (13th file). -L is used to run multiple run files at the same time.
