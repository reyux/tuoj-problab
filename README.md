# TUOJ Problem Lab

This is the submodules ProblemLab of TUOJ.

## Progress

+ prob format (fin.)
+ deploy (ing.)
+ gitlab
	+ omniauth
	+ limitation

## Prob Format

A problem sample is showed in ProbSample.

The essential directory structure：

	- problem
		- files			\\ the files irrelevant to deployment, judgement and so on, like description, tutorial, etc.  
		- source		\\ source code of judger, validator, generator, etc. 
		- data			\\ the data for judgement
			[- data.gen]	\\ you can use script to generate a data set, with the `.gen` suffix.  
		- etc			
			- conf.json		\\ a json file contains the problem's details
			- deploy.init	\\ the deploy script
		[- test] 		\\ the submission for testing
		[- your other files: README.md, etc.]

### config

(to be finished)

### generate data

<http://polygon.codeforces.com> allows a dynamic way to provide data using a generating script. Here we reserve the interface as the `.gen` file in `data`.

## Deploy

You may need to do some initilization after clone as there is usually no executable file but the source code stored in repository.
Actually you cannot modify anything in workdir or unexcepted error will be raised when pulling update or doing other git operations, 
hence you must create a new folder at somewhere outside, copying those source codes into it and building the judge environment.

`etc/deploy.init` states the deployment, with each line contains a single command. Here two commands maybe useful are showed below. You may need to see `ProbSample/etc/deploy.init` for more details.

	compile <file>		\\ compile source/<file> in term of its suffix.
	make <makefile>		\\ use source/<makefile> to initialize, this command should be limited at server.

In ServerSample we give a python sample `deploySample.py` to interpret the script.

## Testing

(to be finished)

