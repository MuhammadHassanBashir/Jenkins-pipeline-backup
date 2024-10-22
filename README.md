# Jenkins-pipeline-backup

I need to create backups for my Jenkins pipeline to secure the Jenkins server against any potential mishaps. My Jenkins server is running on a GCP VM, so I created a snapshot schedule in GCP and attached it to the Jenkins VM disk. The snapshot scheduler will run daily at 5 AM, taking a snapshot of the Jenkins server disk and saving it to the GCP Snapshots section

## Steps to Attach a Snapshot Schedule to the Jenkins Server Disk

To ensure consistent backups of your Jenkins server running on a Google Cloud VM, you can attach a snapshot schedule to the disk associated with your Jenkins VM. The schedule will take daily snapshots of the disk and store them in Google Cloud for future recovery in case of mishaps.

Step-by-Step Process:
---------------------

-  Go to the Disks Page:


  In the Google Cloud Console, navigate to the Disks page.

-  Select the Disk:

  From the list of disks, select the name of the disk you want to attach the snapshot schedule to. In this case, the disk is named jenkins-europe. This will open the Manage Disk page.

-  Edit Disk Settings:

  On the Manage Disk page, click the Edit button to modify the disk’s configuration.

-  Attach Snapshot Schedule:

  In the Snapshot Schedule section, use the drop-down menu to select an existing snapshot schedule.
  Alternatively, you can create a new schedule for the disk by selecting the "Create New Schedule" option.

-  Configure the Snapshot Schedule:

      If creating a new schedule, you will be taken to the Snapshot Scheduler page. Provide the following information:
      
      **Name**: Provide a descriptive name for the schedule.
      
      **Description**: Optionally, add a description of the schedule for future reference.
      
      **Snapshot Storage Location**: Choose either Multi-regional or Regional storage, depending on your redundancy needs.
      
      **Schedule Options**:
      
      **Schedule Frequency**: Set the frequency to Daily.
      **Start Time (UTC)**: Set the time to 8:00 AM - 9:00 AM UTC (you may adjust based on your needs).
      **Autodelete Snapshots After**: Set the retention period (e.g., 7 days).
      Deletion Rule:
      
      **Choose Keep snapshots to retain snapshots even after the disk is deleted.
      
Application Consistency (Optional): disable this other wise schedular will not work. I have test this.
      
      Disable Application Consistent Snapshots if you want to ensure that all pending writes on the disk are flushed before a snapshot is taken. This uses guest flush or VSS, ensuring consistent backups when the disk is in use.
      
      **Snapshot Labels**: Optionally, add labels to the snapshot for easy identification and management.

-  Create the Schedule:

    After filling out the necessary fields, click Create to finalize the snapshot schedule.

-  Save Changes to the Disk:

    Go back to the Manage Disk page and click Save to attach the snapshot schedule to your Jenkins server disk.
