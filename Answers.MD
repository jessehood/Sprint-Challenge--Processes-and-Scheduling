1.  
  - Running: The process is either ready or is already running.
  - Waiting: The process is waiting for something (e.g. stdin, I/O) or sleeping
  - Stopped: The process is stopped
  - Zombie:  See description below

2. The process is stopped but still exists in the process table; probably the result of a fork and the OS holding onto information (exit status) about the child that the parent may want to access. The zombie process can be killed by killing the parent or sending a `SIGCHLD` signal.

3. The scheduler is responsible for scheduling processes to run. It is able to assign process a priority level which will allow for processes to be run in a desired order. Higher priority process will also get more execution time than lower priority processes.

4. A multilevel feedback queue will push process taking too much time to a lower priority. It will also push lower priority processes that have been waiting a long time to a higher priority. A round robin queue may cause unresponsiveness because system processes have the same priority as all other processes.