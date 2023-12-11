The system is combined of 3 modules:

**DTO (Data Transfer Object):**
details from the engine system which are transferred to the graphic user interface as Strings and Objects. Thanks to that, we can show these details to the user on the screen, without having the ability to update them.

**SystemGUI:**
Where all the graphic user interface is managed. Hierarchy: App controller includes Header controller and Body controller. Body controller includes Details controller, NewExecution controller and Results controller. Details controller includes all the data that is shown to the user about the World that is loaded from the current xml file (actions, environments, entities, properties, etc.). NewExecution controller manages user inputs (entities population and environments values) that will be the initialized values for the new execution. Results controller includes executions list (all the simulations that have been executed by the user), simulation details (status, current ticks, and current seconds. In there the user can choose to stop, resume, or pause the simulation, and the user can see the current population for each entity in runtime. In addition, there's also the simulation results which would be shown after the chosen execution is finished. There the user can see for each property the histogram, population graph, consistency and average (only if the property is numeric). Also, the user can choose to rerun a finished execution.

In addition to that, there's a thread which sleeps every 300 milliseconds and withdraws DTO from the chosen simulation, so the user would be able to see its details.

**SystemInterface:**
Holds all the functions that the user willing to execute and running the whole related simulation.

• SimulationExecutionManager: In charge of all the simulations, such as: providing their details as DTO, stopping/starting simulation, creating and setting details before running a simulation, etc. 

• SimulationExecutionDetails: Every execution that we run has its own simulation execution details which holds its properties and details. 

• SimulationRunner: A class that implements Runnable class. This class runs a simulation using a thread from the thread pool. In addition to these classes, we have classes for each detail in a simulation (rules, entities, environments, etc). Also – World class Holds the details of each entity, environment, property to be used in the simulation.


*** Where we show the graph of population per ticks, we chose to show only every 1000 ticks and the x axis is up to 100.
We chose that because there's a lot of data loaded to the graph (many ticks pass), which makes the system work slow.
