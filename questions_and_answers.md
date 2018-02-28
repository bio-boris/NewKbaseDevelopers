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
[User Inferface Parameter Gallery](https://narrative.kbase.us/narrative/ws.23109.obj.1)

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
