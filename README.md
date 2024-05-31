# FTP Service Scheduler (FSS)

FTP Service Scheduler (FSS) is a web-based application designed to automate the scheduling of FTP jobs. Initially developed for the Business Intelligence team, FSS helps streamline and automate ETL (Extract, Transform, Load) processes by managing file transfers efficiently.

## Features

- Schedule and automate FTP jobs
- Retry mechanism for handling temporary failures
- Email notifications for job success or failure
- File transfer to multiple destinations
- Trigger file creation to signal ETL process initiation

## Example Workflow

1. **Data Extraction**: 
   - The AS400 system executes a scheduled job to perform a data extraction. The extraction is saved as a flat file on disk.

2. **Job Scheduling**: 
   - FSS schedules a workflow with a specified time, retry attempts, source location, destination location, and a trigger file name.

3. **File Monitoring and Retries**: 
   - FSS checks the AS400 disk for the presence of the completed file, retrying until the retry limit is reached. If the limit is reached, an email notification is sent indicating job failure.

4. **File Transfer**:
   - On successful file detection, all files are transferred to the FSS server and then to the designated destination. If the destination connection fails, an email notification is sent indicating the failure.

5. **Trigger File Creation**:
   - After successful file transfer, a trigger file is created to notify the ETL process to begin processing the files.

