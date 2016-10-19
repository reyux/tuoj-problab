# TUOJ Problem Lab

This is the submodules ProblemLab of TUOJ.

(suspend until at least Nov. 15th)

## Progress

+ prob format (fin.)
+ deploy (ing.)
+ gitlab
	+ omniauth
	+ limitation

## Prob Format

A problem sample is showed in ProbSample.

The essential directory structure：

	- git_repo
		- files			\\ the files irrelevant to deployment, judgement and so on, like description, tutorial, etc.  
		- source		\\ source code of judger, validator, generator, etc. 
		- data			\\ the data for judgement
			[- data.gen]	\\ you can use script to generate a data set, with the `.gen` suffix.  
		- etc			
			- conf.json		\\ a json file contains the problem's details
			- deploy.init	\\ the deploy script
		[- test] 		\\ the submission for testing
		[- your other files: README.md, etc.]
	- core				\\ the environment for judgement
	- usr				\\ files generated after deployment

### config

As you see, only directory structure is not enough to describe a problem, and `etc/conf.json` finishs the rest work.
It is a json files that contains the details like which is the statement file, where is the special judge, what is the time/memory limitation and so on. 

`ProbSample` shows a sample with some default values, and actually it can have any form, as the interpretator is custom, but we recommend you to use the default values to declare those info frequently used.

See `CONFIG.md` for more details.

### Dynamic Data Providing

You may not be able to upload large data as the space is usually limited in remote repo. 
<http://polygon.codeforces.com> allows a dynamic way to locally generate them using custom generator, and here we reserve the interface as the `.gen` file in `data`. The script should have the same form as that in polygon.

Those data will be generated and saved in `usr\dynamic_data` if manually call it or before a set of submits comes, if it is the latter those data will be removed after judgement.

## Deploy

You may need to do some initilization after clone as there is usually no executable file but the source code stored in repository.
Actually you cannot modify anything in workdir or unexcepted error will be raised when pulling update or doing other git operations, 
hence you must create a new folder at somewhere outside, copying those source codes into it and building the judge environment.
We use `core` to denote it in directory structure.

`etc/deploy.init` states the deployment, with each line contains a single command. Here two commands maybe useful are showed below. You may need to see `ProbSample/etc/deploy.init` for more details.

	compile <file>			\\ compile source/<file> in term of its suffix.
	mktest 	<file>			\\ make a test submit using <file>

In ServerSample we give a python sample `deploySample.py` to interpret the script.

## Testing

Usually a problem will have some submits to test, and you may would like to use them to test whether the problem is correctly built, e.g., the data is correctly generated.
It is recommended to place those submits be in `test` for convenience. 
Some code that may be used in judgement, like standard solution, can be placed in `source` initially and use `mktest` in `etc/deploy.init` to declare. 


