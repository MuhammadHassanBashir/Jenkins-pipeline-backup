# Jenkins-pipeline-backup

I need to create backups for jenkins pipeline for securing jenkins server for any mishaps. My jenkins server is running in gcp vm. So what i did, i created a snapshot schedule in gcp and attached this snap schedule with jenkins vm disk.
the snap scheduler will run on every day at 5am and will take the jenkins server disk snapshot and save it to gcp snapshot section. 

## Steps to Attach a Snapshot Schedule to the Jenkins Server Disk

To ensure consistent backups of your Jenkins server running on a Google Cloud VM, you can attach a snapshot schedule to the disk associated with your Jenkins VM. The schedule will take daily snapshots of the disk and store them in Google Cloud for future recovery in case of mishaps.

Step-by-Step Process:
---------------------

1.  Go to the Disks Page:
------------------------

  In the Google Cloud Console, navigate to the Disks page.

2.  Select the Disk:
--------------------

  From the list of disks, select the name of the disk you want to attach the snapshot schedule to. In this case, the disk is named jenkins-europe. This will open the Manage Disk page.
3.  Edit Disk Settings:

  On the Manage Disk page, click the Edit button to modify the disk’s configuration.
4.  Attach Snapshot Schedule:

  In the Snapshot Schedule section, use the drop-down menu to select an existing snapshot schedule.
  Alternatively, you can create a new schedule for the disk by selecting the "Create New Schedule" option.
5.  Configure the Snapshot Schedule:

      If creating a new schedule, you will be taken to the Snapshot Scheduler page. Provide the following information:
      
      Name: Provide a descriptive name for the schedule.
      
      Description: Optionally, add a description of the schedule for future reference.
      
      Snapshot Storage Location: Choose either Multi-regional or Regional storage, depending on your redundancy needs.
      
      Schedule Options:
      
      Schedule Frequency: Set the frequency to Daily.
      Start Time (UTC): Set the time to 8:00 AM - 9:00 AM UTC (you may adjust based on your needs).
      Autodelete Snapshots After: Set the retention period (e.g., 7 days).
      Deletion Rule:
      
      Choose Keep snapshots to retain snapshots even after the disk is deleted.
      Application Consistency (Optional):
      
      Enable Application Consistent Snapshots if you want to ensure that all pending writes on the disk are flushed before a snapshot is taken. This uses guest flush or VSS, ensuring consistent backups when the disk is in use.
      Make sure your guest VM supports this feature.
      Snapshot Labels: Optionally, add labels to the snapshot for easy identification and management.

6.  Create the Schedule:

    After filling out the necessary fields, click Create to finalize the snapshot schedule.
7.  Save Changes to the Disk:

    Go back to the Manage Disk page and click Save to attach the snapshot schedule to your Jenkins server disk.
