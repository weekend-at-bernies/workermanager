WorkerManager.py exposes Python classes for you to use so that you can:

- Create a bunch of worker threads that can work in parallel to do some common piece of work, on 
  individual pieces of data.
- Create a "worker manager" to "oversee" the workers.

Refer to 'Example.py' to get you going.

In 'Example.py' we create:

- A "thread" worker manager (ie. the workers will be threads of the same process).
- A "process" worker manager (ie. the workers will be different processes).

Each worker manager will oversee 10 workers.
The job of each worker is to simply print out:
- Their "identity".
- Their worker number (1 to 10).

Each worker's "identity" is a randomly assigned name (eg. "TurgidTurbin").
Passing in a seed value to 'Example.py' at the command-line ensures that 
the worker identities are deterministic. 

When we execute 'Example.py', the worker managers will get their workers
to do their work 5 times, giving us 5 pieces of output we can compare 
against one another.

Look at the output below. Some observations:

- Thread workers get their job done faster than their process worker counterparts. This is due
  to the work required to be performed in 'Example.py', which favours running in a thread context
  rather than in a separate process.

- The order in which workers finish is NOT deterministic. For example consider:

  ObtuseFollicle (2 of 10): 98
  IntrepidReindeer (4 of 10): 83

  Worker 4 (IntrepidReindeer) finishes before worker 3.

-----------------------------------------------------------------------

$ python Example.py 50

THREAD WORKERS:
TurgidTurbin (1 of 10): 64
ObtuseFollicle (2 of 10): 98
KineticReindeer (3 of 10): 68
IntrepidReindeer (4 of 10): 83
KineticPopsicle (5 of 10): 19
KineticPopsicle (6 of 10): 60
ChromiumCarrot (7 of 10): 92
NebulousPopsicle (8 of 10): 83
ChromiumFandangle (9 of 10): 43
TurgidViper (10 of 10): 93
DURATION: 0.001550

PROCESS WORKERS:
TurgidTurbin (1 of 10): 64
ObtuseFollicle (2 of 10): 98
IntrepidReindeer (4 of 10): 83
KineticPopsicle (6 of 10): 60
ChromiumCarrot (7 of 10): 92
NebulousPopsicle (8 of 10): 83
KineticPopsicle (5 of 10): 19
KineticReindeer (3 of 10): 68
ChromiumFandangle (9 of 10): 43
TurgidViper (10 of 10): 93
DURATION: 0.007428

------------------

THREAD WORKERS:
TurgidTurbin (1 of 10): 64
ObtuseFollicle (2 of 10): 98
KineticReindeer (3 of 10): 68
 IntrepidReindeer (4 of 10): 83
KineticPopsicle (5 of 10): 19
KineticPopsicle (6 of 10): 60
ChromiumCarrot (7 of 10): 92
NebulousPopsicle (8 of 10): 83
ChromiumFandangle (9 of 10): 43
TurgidViper (10 of 10): 93
DURATION: 0.000942

PROCESS WORKERS:
TurgidTurbin (1 of 10): 64
ObtuseFollicle (2 of 10): 98
KineticReindeer (3 of 10): 68
IntrepidReindeer (4 of 10): 83
KineticPopsicle (5 of 10): 19
KineticPopsicle (6 of 10): 60
NebulousPopsicle (8 of 10): 83
ChromiumCarrot (7 of 10): 92
TurgidViper (10 of 10): 93
ChromiumFandangle (9 of 10): 43
DURATION: 0.004880

------------------

THREAD WORKERS:
ObtuseFollicle (2 of 10): 98
TurgidTurbin (1 of 10): 64
KineticReindeer (3 of 10): 68
 IntrepidReindeer (4 of 10): 83
KineticPopsicle (5 of 10): 19
KineticPopsicle (6 of 10): 60
ChromiumCarrot (7 of 10): 92
 NebulousPopsicle (8 of 10): 83
ChromiumFandangle (9 of 10): 43
TurgidViper (10 of 10): 93
DURATION: 0.001120

PROCESS WORKERS:
TurgidTurbin (1 of 10): 64
ObtuseFollicle (2 of 10): 98
KineticReindeer (3 of 10): 68
IntrepidReindeer (4 of 10): 83
KineticPopsicle (5 of 10): 19
KineticPopsicle (6 of 10): 60
ChromiumCarrot (7 of 10): 92
NebulousPopsicle (8 of 10): 83
ChromiumFandangle (9 of 10): 43
TurgidViper (10 of 10): 93
DURATION: 0.004191

------------------

THREAD WORKERS:
TurgidTurbin (1 of 10): 64
ObtuseFollicle (2 of 10): 98
KineticReindeer (3 of 10): 68
IntrepidReindeer (4 of 10): 83
 KineticPopsicle (5 of 10): 19
KineticPopsicle (6 of 10): 60
ChromiumCarrot (7 of 10): 92
NebulousPopsicle (8 of 10): 83
ChromiumFandangle (9 of 10): 43
TurgidViper (10 of 10): 93
DURATION: 0.001171

PROCESS WORKERS:
TurgidTurbin (1 of 10): 64
ObtuseFollicle (2 of 10): 98
KineticReindeer (3 of 10): 68
IntrepidReindeer (4 of 10): 83
KineticPopsicle (5 of 10): 19
KineticPopsicle (6 of 10): 60
ChromiumCarrot (7 of 10): 92
NebulousPopsicle (8 of 10): 83
ChromiumFandangle (9 of 10): 43
TurgidViper (10 of 10): 93
DURATION: 0.004230

------------------

THREAD WORKERS:
TurgidTurbin (1 of 10): 64
ObtuseFollicle (2 of 10): 98
 KineticReindeer (3 of 10): 68
IntrepidReindeer (4 of 10): 83
 KineticPopsicle (5 of 10): 19
KineticPopsicle (6 of 10): 60
ChromiumCarrot (7 of 10): 92
NebulousPopsicle (8 of 10): 83
ChromiumFandangle (9 of 10): 43
TurgidViper (10 of 10): 93
DURATION: 0.000825

PROCESS WORKERS:
TurgidTurbin (1 of 10): 64
ObtuseFollicle (2 of 10): 98
KineticReindeer (3 of 10): 68
IntrepidReindeer (4 of 10): 83
KineticPopsicle (5 of 10): 19
KineticPopsicle (6 of 10): 60
ChromiumCarrot (7 of 10): 92
NebulousPopsicle (8 of 10): 83
ChromiumFandangle (9 of 10): 43
TurgidViper (10 of 10): 93
DURATION: 0.004021

-----------------------------------------------------------------------


