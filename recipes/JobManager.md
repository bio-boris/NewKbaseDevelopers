## How to view latest jobs
    from biokbase.narrative.jobs.jobmanager import JobManager
    jm = JobManager()
    jm.list_jobs()

## If you do run_app() without a cell_id field, it’ll return the job object. So you could do something like:
    
    my_job = AppManager().run_app( ... app info ...)
    my_job.job_id
