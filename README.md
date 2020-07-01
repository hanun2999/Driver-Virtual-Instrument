# Driver-Virtual-Instrument
## Execute
### Download
[CLI Client zip](../master/labforward_cli.zip?raw=true)
### Linux / Mac from a Terminal Window:
```bash
$ node driver.js
```
or (in labforward_cli directory)
```bash
$ driver
``` 
Follow the instructions presented within the CLI

<img src="https://github.com/Eduard53/Driver-Virtual-Instrument/blob/master/CLI.png" width="700">

	
### Commands
```bash
	help, h		Dispaly help menu
	I		Display device information
	S		Obtain stable weight
	end, quit, q	Quit the process
```
	
### Dependencies
Dependencies are located in the modules folder
* ESM
* JEST

## Definition of Completion

The project is completed to the standard of the documentation provided by illustrating the following requirements.

The `driver.js` (parent) is the primary driver file for communicating asynchronously with the virtual_instrument.js (child) virtual balance in this instance.
This is done by creating a new child object using the '.fork' which is an asynchronous communication Inter Process Communication (IPC) stream. Commands can 
be sent via running the main node driver.js. The driver sends a message to the child (virtual_instrument.js) which then randomly simulates a result. 
The driver.js is an interactive Command Line Interface (CLI) whereby, the user can dynamically enter commands and interact with the virtual instrument. 

The virtual_instrument.js (child) is simulating a virtual balance that sends the data to the driver.js (parent) when requested. The stable weight value in this 
example is calculated by averaging a simulated number of 10 samples. This is to simulate the fluctuations that may occur whilst the balance is stabilizing. Any 
input value that is received will be converted to a hexadecimal [0x] value and displayed on the CLI. The response from the virtual balance will also be randomised 
according to the documentation for the command. e.g. 
```bash
S I
S S    x.g
S +
S -
```
The virtual instrument is also responsible for logging and recording the results 
obtained from a successful reading of the balance to a text file.

## Unit Tests

Unit tests have also been performed on a few of the functions utilising JEST. 
To run the unit tests, be sure to be in the directory of 'labforward_cli' and run:
```bash
$ npm test
```
<img src="https://github.com/Eduard53/Driver-Virtual-Instrument/blob/master/JEST.png" width="240">
