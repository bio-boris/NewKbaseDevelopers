# FileUtil Recipes
## Need to work with a type of file? Use a built in utility for that. 

### How?
*Search for "Util" at https://ci.kbase.us/#catalog/modules

# DataFileUtil and GenomeFileUtil recipes

DFU and GFU are very commonly used, so check out examples below


## About DataFileUtil
* [DataFileUtils](https://github.com/kbaseapps/DataFileUtil) is the preferred way to retrieve and save objects, as well as uploading files and receiving an unique identifier once they are in our system.

## Initialize DataFileUtil Client and get an object by reference.
    self.callback_url = config["SDK_CALLBACK_URL"]
    self.dfu = DataFileUtil(self.callback_url)
    genome_ref = "your/object_reference"
    genome_data = dfu.get_objects({'object_refs': [genome_ref]})['data'][0]
    genome_obj = genome_data['data']
    genome_meta = genome_data['info'][10]

    
## Upload a file or directory to shock 
    #Upload a directory and zip it
    directory_file_path = "/kb/module/data/"
    shock_id = self.dfu.file_to_shock({"file_path": directory_file_path, "pack": "zip"})["shock_id"]
    
    #Upload a file to shock
    file_path = "/kb/module/data/"
    shock_id = self.dfu.file_to_shock({"file_path": file_path})["shock_id"]
    

## Save an object to the workspace and get an object reference
    self.workspace_name = params.get("workspace_name")
    workspace_id = self.dfu.ws_name_to_id(self.workspace_name)
    save_object_params = {
        'id': workspace_id,
        'objects': [{
            'type': 'KBaseRNASeq.RNASeqSampleSet',
            'data': sample_set_data,
            'name': sample_set_object_name
        }]
    }

    dfu_oi = dfu.save_objects(save_object_params)[0]
    object_reference = str(dfu_oi[6]) + '/' + str(dfu_oi[0]) + '/' + str(dfu_oi[4])

## Save an object from shock to filepath
    #TODO
    self.dfu.shock_to_file({'handle_id': handle_id,
                        'file_path': tmp_gtf_directory,
                        'unpack': 'unpack'})
                        
# GenomeFileUtils Recipes
    #TODO
    Set up an assembly for all of your tests, otherwise a genome object wont work because it has an assembly ref that may not exist on the appdev/ci workspaces. 

# 
