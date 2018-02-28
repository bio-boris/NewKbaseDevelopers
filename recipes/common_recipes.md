# Common Recipes
Sometimes you don't want to look at the spec file or go to the kb_apps repo to figure out how to do something,
you just want an answer quickly.


# Workspace Recipes

## About the workspace
* While you can get objects form the workspace, it is not the preferred way to do it. We suggest using DataFileUtils instead.
However, if you don't want to retrieve the entire object, and just want information about it, use ws.get_object_info .
If you wan't to read more about the available functions, see the spec file and search through the repository at 
[Workspace Deluxe](https://github.com/kbase/workspace_deluxe)



## Initialize Workspace Client and get an object's information by reference
    from Workspace.WorkspaceClient import Workspace as Workspace
    self.ws_url = config["workspace-url"]
    self.token = config["KB_AUTH_TOKEN"]
    self.ws = Workspace(self.ws_url, token=self.token)
    obj_ref = "your/object/reference"
    object_info = self.ws.get_object_info([{"ref": obj_ref}])[0]
    object_type = object_info[2] #this could be KBaseGenomes.Genome-8.3
    
# DataFileUtils Recipes

## About DataFileUtil
* [DataFileUtils](https://github.com/kbaseapps/DataFileUtil) is the preferred way to retrieve and save objects, as well as uploading files and receiving an unique identifier once they are in our system.

## Initialize DataFileUtil Client and get an object by reference.
    self.callback_url = config["SDK_CALLBACK_URL"]
    self.dfu = DataFileUtil(self.callback_url)
    genome_ref = "your/object_reference"
    genome_data = dfu.get_objects({'object_refs': [genome_ref]})['data'][0]
    genome_obj = genome_data['data']
    genome_meta = genome_data['info'][10]
    
    
                self.dfu.shock_to_file({'handle_id': handle_id,
                                    'file_path': tmp_gtf_directory,
                                    'unpack': 'unpack'})
    
## Upload a file or directory to shock 
    #Upload a directory and zip it
    directory_file_path = "/kb/module/data/"
    shock_id = self.dfu.file_to_shock({"file_path": directory_file_path, "pack": "zip"})["shock_id"]
    #Upload a file to shock
    file_path = "/kb/module/data/"
    shock_id = self.dfu.file_to_shock({"file_path": file_path})["shock_id"]
    
    

## Save an object to the workspace and get an object reference

    new_obj_info = self.ws.save_objects({
            "workspace": self.workspace_name,
            "objects": [{
                "type": "KBaseSequences.SequenceSet",
                "data": {"sequence_set_id": sequence_set_id, "description": sequence_set_description,
                         "sequences": sequences},
                "name": "seqset_" + str(uuid.uuid4())
            }]
        })[0]

        return {"ref": str(new_obj_info[6]) + "/" + str(new_obj_info[0]) + "/" + str(new_obj_info[4]),
                "description": "Sequence Set for " + output_filename}




# GenomeFileUtils Recipes


# Generate a Report Recipes (requires correct widget settings)
