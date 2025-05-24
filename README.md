# EC2-LVMSnapshotBackup-Restore
Automated Backup and Restore of EC2 LVM Volume Using AWS Snapshots

## Overview

This project demonstrates how to manage storage on an AWS EC2 instance using **LVM (Logical Volume Manager)** and how to perform **backup and restore** operations using **Amazon EBS snapshots**.

It's a practical DevOps use case that shows how to handle disaster recovery and persistent data in cloud environments.

---

## Technologies Used

- **AWS EC2**
- **Amazon EBS Snapshots**
- **Linux (Amazon Linux 2 / Ubuntu)**
- **LVM2 (Logical Volume Manager)**
- **Bash Shell**

---

## Objectives

- Configure LVM on an EC2 instance
- Write and store data in a logical volume
- Create a snapshot of the volume
- Launch a new EC2 instance and restore from snapshot
- Verify data recovery from the restored volume

---

## Steps Performed

### 1. Launch EC2 Instance

- OS: Amazon Linux 2
- Instance Type: `t2.micro` (Free Tier)
- SSH Access enabled

### 2. Attach and Configure EBS Volume

- Created 1 GiB EBS volume and attached to instance as `/dev/xvdf`
- Initialized as Physical Volume (PV)
- Created Volume Group (VG): `myvg`
- Created Logical Volume (LV): `mylv` (500MB)
- Formatted as ext4 and mounted to `/mnt/mydata`

### 3. Add Sample Data

```bash
echo "Hello from LVM!" | sudo tee /mnt/mydata/hello.txt
