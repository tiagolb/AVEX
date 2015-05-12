# AVEX
Avex Project

How to compile FCEUX
 - install dependencies: sudo apt-get install libsdl1.2-dev scons libgtk-3-dev liblua5.1-0-dev
 - enter FCEUX's folder: cd fceux-2.2.1
 - this may need to be done: vi SConstruct
	Change lines 27 and 28 to look like this.
  		BoolVariable('GTK', 'Enable GTK2 GUI (SDL only)', 0),
  		BoolVariable('GTK3', 'Enable GTK3 GUI (SDL only)', 1),
	This will give us a modern GTK3 interface instead of using the now outdated GTK2 toolkit. Feel free to change any of the other settings if you wish. I turned off the debug symbols. Now we are ready to compile our binary.
 - to compile FCEUX: scons ( this may present warnings... it's ok, warnings are ok :P )

How to run FCEUX
 - enter FCEUX's folder: cd fceux-2.2.1
 - run FCEUX: ./bin/fceux

How to perform fine grained profiling
 - to allow for fine grained profiling (more expensive):
	cd fceux-2.2.1/src/
	vi x6502.cpp
 - in the define section uncomment the #define FINE_PROFILING line
 - then compile FCEUX again and run it
 - when you want the profiling to be writen to a file just go to Emulator > Reset in the emulator window Tab
 - a new file PROFILING.txt will appear
 - this file is a TSV file (although with the extension .txt) that can be imported to Excell for further analysis

How to perform coarse grained profiling
 - to allow for coarse grained profiling (less expensive):
        cd fceux-2.2.1/src/
        vi x6502.cpp
 - in the define section uncomment the #define COARSE_PROFILING line
 - then compile FCEUX again and run it as such: ./bin/fceux > COARSE_PROFILING.txt
 - edit this file and remove the lines corresponding to explicit FCEUX messages (all lines except "clicks" and all the lines with numbers only)
 - the numbers represent the clicks in between 1000000 instructions
 - this file is a TSV file (although with the extension .txt) that can be imported to Excell for further analysis

