Automated Backup and Restore of EC2 LVM Volume Using AWS Snapshots
Overview

This project demonstrates how to manage storage on an AWS EC2 instance using LVM (Logical Volume Manager) and how to perform backup and restore operations using Amazon EBS snapshots.
It is a practical DevOps use case for handling disaster recovery and persistent data in cloud environments.
Technologies Used

    AWS EC2
    Amazon EBS Snapshots
    Linux (Amazon Linux 2 / Ubuntu)
    LVM2 (Logical Volume Manager)
    Bash Shell

Objectives

    Configure LVM on an EC2 instance
    Write and store data in a logical volume
    Create a snapshot of the volume
    Launch a new EC2 instance and restore from snapshot
    Verify data recovery from the restored volume

Steps Performed
1. Launch EC2 Instance

    OS: Amazon Linux 2
    Instance Type: t2.micro (Free Tier)
    SSH Access enabled

2. Attach and Configure EBS Volume

    Create a 1 GiB EBS volume and attach it to the instance as /dev/xvdf
    Initialize as Physical Volume (PV)
    Create Volume Group (VG): myvg
    Create Logical Volume (LV): mylv (500 MB)
    Format as ext4 and mount to /mnt/mydata

3. Add Sample Data
bash

echo "Hello from LVM!" | sudo tee /mnt/mydata/hello.txt

4. Backup with Snapshot

    Unmount the volume:
    bash

    sudo umount /mnt/mydata

    Create an AWS snapshot of the attached EBS volume

5. Restore on New EC2 Instance

    Launch a new EC2 instance in the same AZ
    Create a new EBS volume from the snapshot and attach as /dev/xvdf
    Activate LVM and mount the logical volume:
    bash

sudo vgscan
sudo vgchange -ay
sudo lvdisplay
sudo mount /dev/myvg/mylv /mnt/recovery

Verify the recovered file:
bash

    cat /mnt/recovery/hello.txt

Outcome

Successfully demonstrated:

    LVM configuration and volume management
    EBS snapshot creation and restoration
    Real-world data recovery in AWS

Author

Your Name Here
Cloud & DevOps Learner
License

This project is open-source and free to use.
