## How do I start my app? What do I do now?

1) Work on the implmentaiton file to generate methods

It is recommended to have a spec file look the following:
    (SpecFile Recipes Link)
    
2) Decide on a basic UI layout working backwards with the .spec file

Run Make and Generate the implementation file




### How do I organize the code?

There are two common patterns:
1) Create multiple functions and do everything inside the implmentation file. An example of this pattern can be found in these apps [1,2,3]()
2) Create a utils directory, create a runner or utility class, pass in the configuration file and parameter files to it, and do everything in there. An example of this pattern can be found in these apps [1,2,3]()



### Help! My python code in the implementation file keeps disappearing? What happened to it?
Magic comments are comments that are used internally by the kbase_sdk in order to generate the implementation file when you make changes to the spec file. 

Examples of magic comments include
```
#BEGIN_HEADER
(This is where your import statements go)
#END_HEADER

#BEGIN_CLASS_HEADER
(This is where your class variables and functions go that you want imported)
#END_CLASS_HEADER

#BEGIN_CONSTRUCTOR
(This is in your init statement for your class goes)
#END_CONSTRUCTOR

#BEGIN YourFunctionName1
(This is were the implementation details of your functions go)
#END YourFunctionName1
```
Any code created outside of the Magic Comments will not be included inside the final .impl implementation file.

# Validation
### Q: How does validation work for apps? 

Currently validation is done in the UI based on values provided in the ui/narrative/methods/spec.json. 
When invalid input is entered in the UI for the app, an error will display to the user,
and the user will not be able to submit the form for the app.

Validation is not provided for the app to be called programmatically (such as with unit tests)
so you will have to validate your input again. 
It may be possible to generate validation programmatically using the spec.json file,
but this is not currently an out of the box feature.

### Q: How do I learn more about the spec.json file?
While there isn't a document with all of the valid UI Parameters, 
you can check out this notebook with a variety of different options at
[User Inferface Parameter Gallery](https://narrative.kbase.us/narrative/ws.23109.obj.1). Also see [Narrative UI Specification](https://github.com/kbase/kb_sdk/blob/master/doc/NarrativeUIAppSpecification.pdf)

# Docker

### Q: Should I always specify a specific version of a library or executable ?

There is not currently a requirement to use a specific version, but the tradeoff is as follows:
When using a specific version of a library or executable, you don't have to worry as much about backwards comptability with future releases.
However, if a newer version of the software is available, your app won't automatically use it. 

### Q: Where do I install binaries in docker?

You can install binaries that will automatically be added to $PATH at /kb/deployment/bin, like so

    #Install Diamond Binary v0.9.17
    WORKDIR /kb/deployment/bin
    RUN wget https://github.com/bbuchfink/diamond/releases/download/v0.9.17/diamond-linux64.tar.gz \
    && tar -xvf diamond-linux64.tar.gz diamond \
    && rm diamond-linux64.tar.gz
  
Please follow the [edit dockerfile](https://github.com/kbase/kb_sdk/blob/master/doc/kb_sdk_local_test_module.md#a-edit-dockerfile)
section of the kb-sdk guide.

### Q: How do I get inside the docker image? How do I get root access?

You are supposed to be able to be logged in with sudo access when you run the test_local/run_bash.sh script. If that’s not working, try changing the --user parameter to `--user 0`

### Q: Tell me about the .sh scripts in the test_local directory?
You don't really need anything besides the run_bash.sh script. If you want to run tests, use `kb-sdk test`
