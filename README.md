# pintos - Simple Operating system framework for the 80x86 architecture from Stanford

### Features implemented in the pintos kernel
	- Added file to kernel and tested it
	- Reimplemented timer_sleep mechanism to avoid busy waiting of threads.
	- Priority based scheduling, higher priority threads get scheduled before lower priority threads
	- Mechanism to handle situations where if a current thread lowers its priority, and it no longer is the highest priorty thread, then schedule the highest priority thread from the ready queue.
	- Synchronization - modified implementation of semaphore wait and signal methods to handle cases where, if multiple threads are waiting on a particular semaphore then the thread with the highest priority among them is scheduled first.

### Prerequisites and setup (following steps are for ubuntu)
	- qemu simulator
 	- gcc 4.8 or higher
 	- make sure you have a "qemu" executable in /usr/bin folder, if not then generate a soft link for the same
 	- Edit <path-to-pintos-dir>/src/utils/pintos-gdb file, find and change the line below
 		GDBMACROS=<path-to-pintos-dir>/src/misc/gdb-macros
 	- Edit <path-to-pintos-dir>/src/utils/pintos, find and change line no. 258 to
 		my $name = find_file ('<path-to-pintos-dir>/src/threads/build/kernel.bin');
 	- Edit <path-to-pintos-dir>/src/utils/Pintos.pm, find and change line no. 362 to
 		$name = find_file ("<path-to-pintos-dir>/src/threads/build/loader.bin") if !defined $name;


### Building pintos
	- Under <path-to-pintos-dir>/src/threads folder run :
		make
	this should generate "build" folder in <path-to-pintos-dir>/src/threads directory. 
	- <path-to-pintos-dir>/src/threads/build folder has kernel.o i.e the compiled kernel executable

### Running pintos		
	- cd <path-to-pintos-dir>/src/utils
	- ./pintos -- run <name-of-test-case>
		e.g pintos -- run alarm-multiple
	- You may add "<path-to-pintos-dir>/src/utils" to PATH variable to access "pintos" globally

### Running test cases
	- cd <path-to-pintos-dir>/src/threads/build
	- Run below command :
		make tests/threads/<name-of-test-case>.result SIMULATOR=qemu TIMEOUT=40
	e.g:	make tests/threads/alarm-multiple.result SIMULATOR=qemu TIMEOUT=40

### Credits and references
	https://pintosiiith.wordpress.com/2012/09/13/install-pintos-with-qemu/
	http://web.stanford.edu/class/cs140/projects/pintos/pintos_1.html

