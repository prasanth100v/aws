# 🚀 AWS EBS (Elastic Block Store) 
## 📌 What is AWS EBS?
Amazon EBS (Elastic Block Store) is a **scalable, high-performance block storage service** designed for use with EC2 instances. 
It provides **persistent storage**, meaning your data remains safe even when instances are stopped.

👉 Think of EBS like a hard disk (SSD/HDD) attached to your virtual machine.
   * ✔ Persistent
   * ✔ Fast
   * ✔ Reliable

### 🖼️ How EBS Works (Architecture)
  * 👉 EBS volume is attached to an EC2 instance like a disk
  * 👉 Data stays safe even if the instance stops

## 🔑 Key Features of AWS EBS
| 🧩 Feature            | 💡 Description                                                                            |
| --------------------- | ----------------------------------------------------------------------------------------- |
| 💾 Persistent Storage | 📦 Data remains safe even if EC2 is stopped or restarted (Unlike temporary storage)          |
| 🌍 AZ Bound           | 📍 EBS volume exists in one Availability Zone only (Cannot directly attach to EC2 in another AZ.)    |
| 📸 Snapshots          | ☁️ Snapshots are stored in **Amazon S3**. Used for: backup & restore, Migration across regions & Disaster recovery      |
| 🔐 Encryption         | 🛡️ Data encrypted at rest, in transit, and in snapshots using AWS Key Management Service |


### ❗ Can you reduce (shrink) an AWS EBS volume?
   NO ❌, In Amazon EBS, you cannot decrease (shrink) the size of an existing volume.


------------------------------------------------------------------------

## 📦 EBS Volume Types

### ⚡ High Performance SSD Options
| 🧩 Type                       | 📌 Description            | 💡 Key Details                                    |
| ----------------------------- | ------------------------- | ------------------------------------------------- |
| 🟢 General Purpose SSD (gp2)  | ⚖️ Balanced performance   | 📊 ~3 IOPS per GB (up to 16,000 IOPS)             |
| 🟢 General Purpose SSD (gp3)  | 🚀 Modern, cost-efficient | 🔄 Independent IOPS & throughput scaling          |
| 🔵 Provisioned IOPS SSD (io1) | 🎯 High performance       | 🏦 Designed for critical workloads                |
| 🔵 Provisioned IOPS SSD (io2) | 🔥 Extreme performance    | ⚡ Up to 256,000 IOPS & 4,000 MB/s (Block Express) |


### 🧊 HDD (Low Cost)
| 🧩 Type                           | 📌 Description         | 💡 Best Use Cases                                      |
| --------------------------------- | ---------------------- | ------------------------------------------------------ |
| 🟡 Throughput Optimized HDD (st1) | 📊 High throughput HDD | 📈 Big data, 📝 log processing, 🎥 streaming workloads |
| ⚪ Cold HDD (sc1)                  | 💰 Lowest cost HDD     | 🗂️ Archive data, 📦 rarely accessed data              |

------------------------------------------------------------------------

## ⚙️ Performance Concepts
| 🧩 Concept          | 📌 Description                        | 💡 Key Insight                                  |
| ------------------- | ------------------------------------- | ----------------------------------------------- |
| 📊 IOPS             | 🔢 Input/Output Operations Per Second | ⚡ SSD → High IOPS (fast operations)<br>🐢 HDD → Lower IOPS |
| 🚀 Throughput       | 📈 Data transfer speed (MB/s)         | 📦 Important for large data transfers (HDD volumes optimized for throughput)     |
| ⚡ Burst Performance | 🔄 Temporary performance boost        | 🚀 gp2 supports temporary high performance bursts    |

* 🔢 IOPS                      :  (Speed of operations : 👉 Number of read/write operations per second)
* 📦 Throughput (Data speed    : Measured in MB/s)
* 💥 Burst Performance         : gp2 volumes can temporarily boost speed
------------------------------------------------------------------------

## 🔄 Resize Without Downtime
-   Modify anytime:
    -   Volume size
    -   IOPS
    -   Throughput
    -   Volume type (gp2 → gp3 etc.)
-   No need to stop EC2 instance

## 🔌 Attach & Detach
-   Attach volume to running EC2 👉 No need to stop the server
-   Detach and reattach anytime (You can reattach it to the same or different EC2 (within the same AZ))

### 🔗 Multi-Attach
-   io1/io2 volumes can attach to multiple EC2 instances (same AZ)

## 🔁 Backup & Restore
-   Snapshots used to:
    -   Restore volumes
    -   Create new volumes
    -   Copy across regions

## 💰 Pricing Factors
You pay based on: 
 * 📦 Storage (GB/month)
 * ⚡ Provisioned IOPS (io1/io2)
 * 📸 Snapshot storage (S3)
 * 🌐 Data transfer (if applicable)

------------------------------------------------------------------------

## ⚖️ EBS vs Instance Store
| 🧩 Feature     | 💽 EBS (Elastic Block Store)     | ⚡ Instance Store                     |
| -------------- | --------------------------------- | ------------------------------------  |
| 💾 Persistence | ✅ Yes (data is safe after stop) | ❌ No (data lost on stop/terminate)   |
| 📍 Location    | 🌐 Network attached              | 🖥️ Physically attached (local disk)   |
| 🎯 Use Case    | 📦 Long-term storage             | ⚡ Temporary / cache storage          |


## 🎯 Provisioned IOPS Explained
| 🧩 Scenario                 | 📌 Setup                                                        | 💡 Result                                     |
| ---------------------------- | ---------------------------------------------------------------- | --------------------------------------------- |
| ❌ Without Provisioned IOPS | 💽 Using gp3                                                   | ⚠️ Performance may fluctuate under heavy load |
| ✅ With Provisioned IOPS    | 💽 io1 / io2<br>📦 500 GB<br>⚡ 25,000 IOPS<br>🚀 1,000 MiB/s | 🔥 Consistent, high performance               |

### 💡 Key Benefits
| 🧩 Benefit               | 💡 Explanation                                          |
| ------------------------ | ------------------------------------------------------- |
| ⚡ Consistent Performance | 📊 No fluctuations even under heavy load                |
| 🚫 No Slowdowns          | 🔄 Stable latency for critical apps                     |
| 🎯 Ideal Use Cases       | 🏦 Banking<br>🛒 E-commerce<br>⚙️ Mission-critical apps |

------------------------------------------------------------------------

## 🌩️ AWS EBS VOLUME CREATION
## 🟢 STEP 1: CREATE EBS VOLUME
  
📍 Go to :
  * 👉 Amazon EC2 Dashboard
  * 👉 Left Menu → Elastic Block Store → Volumes
  * 👉 Click Create Volume

## 🔵 STEP 2: CONFIGURE EBS VOLUME
 ### configuration:
  Volume Type (Choose based on use case) 
  * volume_type: "gp3"                  # ⚡ General Purpose SSD (Recommended)
  * size: "10 GiB"                      # 📦 Minimum: 1 GiB (SSD), 500 GiB (HDD)
  * availability_zone: "ap-south-1a"    # 🌍 Must match EC2 AZ
  * snapshot_id: null                    # 📸 Optional (use existing snapshot)
  * encryption:
    * enabled: true                      # 🔐 Encrypt using AWS KMS
    * kms_key: "default/aws/ebs"
  * tags:
    * Name: "MyEBSVolume"
    * Environment: "Dev"

    action: "Click Create Volume"

## 🟡 STEP 3: ATTACH VOLUME TO EC2
 ### attach_volume:
   * Select created volume
   * Click Actions → Attach Volume
      details:
       * instance_id: "i-xxxxxxxxxxxx"
       *  device_name: "/dev/xvdf"               # 💡 Linux device name

## 🔴 STEP 4: FORMAT & MOUNT (LINUX)
 ### linux_commands:
  ```hcl
    lsblk                                     # 🔍 List all disks    # 👉 You’ll see something like: xvda  (root disk) & xvdf  (new EBS volume)
  
    sudo mkfs -t ext4 /dev/xvdf               # 🧱 Format the volume  (Prepares disk for use ) # (ext4 file system)
  
    sudo mkdir /mnt/myvolume                  #📁 Create mount directory #mount point
   
    sudo mount /dev/xvdf /mnt/myvolume        # 🔗 Mount volume   "Attach volume to directory"
 
    df -Th                                    #✅ Verify mount # You should see your new volume
   ```

## 🔄 Optional: Auto Mount on Reboot (Very Important 🚨)
#### 👉 Without this, volume disappears after reboot

### 🔍 Get Volume UUID (Best Practice)
```yaml
sudo blkid
```
Example output: you’ve got the UUID 👍
```hcl
/dev/nvme1n1: UUID="5b0d7452-df2e-4a66-b245-dd12d2449f89" BLOCK_SIZE="4096" TYPE="ext4"
```

Edit fstab: 
 * The file **/etc/fstab** tells Linux: 👉 “Mount this disk automatically when the system starts”
```yaml
sudo nano /etc/fstab
```
Add :
```yaml
UUID=5b0d7452-df2e-4a66-b245-dd12d2449f89   /data   ext4   defaults,nofail   0   2
```
### 🧩 Understanding your entry :
| Field           | Meaning                          |
| --------------- | -------------------------------- |
| `ext4`          | File system type                 |
| `defaults`      | Standard mount options           |
| `nofail`        | ⚠️ Don’t crash if volume missing |
| `0`             | Backup option (ignore)           |
| `2`             | Filesystem check order           |

### 💡 Real-Life Analogy
 * Without fstab → You manually plug USB every time 🔌
 * With `fstab` → USB auto-connects on startup ⚡

### ✅ Test it (VERY IMPORTANT)
```yaml
sudo mount -a
```
  * 👉 No output = `everything correct`
  * 👉 Any error = `fix before reboot`

### 🔄 Reboot
```yaml
sudo reboot
```
### 🔍 Verify after reboot
```yaml
df -h
```
 * You should still see: `/data   mounted ✅`

---

## 🧠 Summary

 - EBS = Persistent, scalable block storage
 - Supports snapshots, encryption, and resizing
 - Multiple volume types for different workloads
 - Essential for production systems on AWS

✨ **Tip:** Use gp3 for most workloads, io2 for critical systems, and `sc1` for cheap storage.
