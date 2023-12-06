# SEAS-core

Package used for connecting external simulations to HELICS and allowing them to run and communicate with each other in a well-defined way.

Contacts are:
- Deepthi Vaidhynathan
- Kinshuk Panda
- Sam Helman

## Installation

SEAS is shipped as a python package and is installable from source via pip. To install:

`pip install https://github.com/NREL/SEAS/blob/main/SEAS.tar.gz?raw=true`


## Usage

In order to use the SEAS library to implement HELICS federates, create a subclass of the `FederateAgent` class that is shipped as part of the SEAS package. Your subclass must implement the following methods:

- `process_periodic_publication`
- `send_periodic_endpoint_messages`
- `process_subscription_messages`
- `process_endpoint_event`

And may optionally implement `publish_initial_helics_data`. See the documentation in the `FederateAgent` class for a full description of these methods.

To use your subclass, do the following (a helics broker must already be running):

1. Instantiate your federate class.
2. Call the `run_helics_setup` method.
3. Call the `enter_execution` method.

The federate will connect to the HELICS broker and run its execution loop for the duration of the simulation, exiting when the simulation is complete. 

For usage examples, see the `examples` folder. The `piexchange` example implements a very simple two-federate simulation that should be useful for new users of SEAS and HELICS.

## Documentation

The class and method documentation is contained inline in the SEAS python files. To view it locally in the browser, run the `view_docs.sh` script.

## Python version

Tested using python 3.8.
