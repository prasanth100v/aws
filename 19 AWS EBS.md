# 🚀 AWS EBS (Elastic Block Store) 
## 📌 What is AWS EBS?
 * Amazon EBS (Elastic Block Store) is a **scalable, high-performance block storage service** designed for use with EC2 instances.
 * It provides **persistent storage**, meaning your data remains safe even when instances are stopped.
 * 👉 Think of EBS like a hard disk (`SSD/HDD`) attached to your virtual machine.
    * ✔ Persistent
    * ✔ Fast
    * ✔ Reliable

### 🖼️ How EBS Works (Architecture)
  * 👉 EBS volume is attached to an EC2 instance like a disk
  * 👉 Data stays safe even if the instance stops

## 🔑 Key Features of AWS EBS
| 🧩 Feature            | 💡 Description                                                                                 |
| --------------------- | ----------------------------------------------------------------------------------------------- |
| 💾 Persistent Storage | 📦 Data remains safe even if EC2 is stopped or restarted (`Unlike temporary storage`)          |
| 🌍 AZ Bound           | 📍 EBS volume exists in `one Availability Zone only` (Cannot directly attach to EC2 in another AZ.)    |
| 📸 Snapshots          | ☁️ Snapshots are stored in **Amazon S3**. Used for: `backup` & `restore`, Migration across regions & Disaster recovery      |
| 🔐 Encryption         | 🛡️ Data encrypted at rest, in transit, and in snapshots using `AWS Key Management Service`           |


### ❗ Can you reduce (shrink) an AWS EBS volume?
  * NO ❌, In Amazon EBS, you cannot decrease (shrink) the size of an existing volume.

---

## 📦 EBS Volume Types
### ⚡ High Performance SSD Options
| 🧩 **Volume Type**       | 📖 **Category**            | 🧠 **Description**                                       | ⚡ **Performance** | 💡 **Best Use Case**                 |
| ------------------------ | -------------------------- | -------------------------------------------------------- | ----------------- | ------------------------------------ |
| 🟢 **gp3**               | General Purpose SSD        | Latest generation SSD with independent IOPS & throughput | High              | Most workloads (recommended)         |
| 🔵 **gp2**               | General Purpose SSD        | Older SSD volume, performance tied to size               | Medium-High       | Legacy workloads                     |
| 🔴 **io2**               | Provisioned IOPS SSD       | High-performance SSD with guaranteed IOPS                | 🚀 Very High      | Mission-critical databases           |
| 🟠 **io2 Block Express** | Ultra-high Performance SSD | Highest EBS performance & durability                     | 🚀🚀 Extreme      | SAP HANA, Oracle, large DBs          |
| 🟡 **st1**               | Throughput Optimized HDD   | Optimized for high throughput workloads                  | High throughput   | Big data, log processing             |
| ⚫ **sc1**                | Cold HDD                   | Lowest-cost HDD storage                                  | Low               | Archives, infrequently accessed data |

### 🧊 HDD (Low Cost)
| 🧩 Type                           | 📌 Description         | 💡 Best Use Cases                                      |
| --------------------------------- | ---------------------- | ------------------------------------------------------ |
| 🟡 Throughput Optimized HDD (st1) | 📊 High throughput HDD | 📈 Big data, 📝 log processing, 🎥 streaming workloads |
| ⚪ Cold HDD (sc1)                  | 💰 Lowest cost HDD     | 🗂️ Archive data, 📦 rarely accessed data              |

---

## ⚙️ Performance Concepts
| 🧩 Concept          | 📌 Description                        | 💡 Key Insight                                  |
| ------------------- | ------------------------------------- | ----------------------------------------------- |
| 📊 IOPS             | 🔢 Input/Output Operations Per Second | ⚡ SSD → High IOPS (fast operations)<br>🐢 HDD → Lower IOPS |
| 🚀 Throughput       | 📈 Data transfer speed (MB/s)         | 📦 Important for large data transfers (HDD volumes optimized for throughput)     |
| ⚡ Burst Performance | 🔄 Temporary performance boost        | 🚀 gp2 supports temporary high performance bursts    |

  * 🔢 IOPS                      : (Speed of operations : 👉 `Number of read/write operations per second`)
  * 📦 Throughput (Data speed    :  Measured in MB/s)
  * 💥 Burst Performance         :  gp2 volumes can temporarily boost speed

---

## 🔄 Resize Without Downtime
   * Modify anytime:
      -   Volume size
      -   IOPS
      -   Throughput
      -   Volume type (`gp2 → gp3` etc.)
      -   `No need to stop EC2 instance`

## 🔌 Attach & Detach
  -   Attach volume to running EC2 👉 No need to stop the server
  -   Detach and reattach anytime (You can reattach it to the same or different EC2 (`within the same AZ`))

### 🔗 Multi-Attach
  -  `io1/io2 volumes` can attach to multiple EC2 instances (`same AZ`)

## 🔁 Backup & Restore
  - Snapshots used to:
     - Restore volumes
     - Create new volumes
     - Copy across regions

## 💰 Pricing Factors
 * You pay based on: 
    * 📦 Storage (GB/month)
    * ⚡ Provisioned IOPS (io1/io2)
    * 📸 Snapshot storage (S3)
    * 🌐 Data transfer (if applicable)

---

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

---

## 🌩️ AWS EBS VOLUME CREATION
## 🟢 STEP 1: CREATE EBS VOLUME
 
  * 📍 Go to : 👉 Amazon EC2 Dashboard
     * 👉 Left Menu → Elastic Block Store → Volumes
     * 👉 Click `Create Volume`

## 🔵 STEP 2: CONFIGURE EBS VOLUME
 * configuration:
 * Volume Type (`Choose based on use case`) 
    * volume_type: "gp3"                           # ⚡ General Purpose SSD (Recommended)
    * size: "10 GiB"                               # 📦 Minimum: 1 GiB (SSD), 500 GiB (HDD)
    * availability_zone: `"ap-south-1a"`           # 🌍 Must match EC2 AZ
    * snapshot_id: `null `                           # 📸 Optional (use existing snapshot)
    * encryption:
       * enabled: `true`                              # 🔐 Encrypt using AWS KMS
       * kms_key: "default/aws/ebs"
    * tags:
      * Name: `"MyEBSVolume"`
      * Environment: `"Dev"`

     * action: "Click Create Volume"

## 🟡 STEP 3: ATTACH VOLUME TO EC2
 ### attach_volume:
   * Select created volume
   * Click Actions → Attach Volume
      * details:
         * instance_id: `"i-xxxxxxxxxxxx"`
         * device_name: `"/dev/xvdf"`                # 💡 Linux device name

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

### 🔍 Get Volume UUID (Universally Unique Identifier) (Best Practice)
```yaml
sudo blkid
```
Example output: you’ve got the UUID 👍
```hcl
/dev/nvme1n1: UUID="5b0d7452-df2e-4a66-b245-dd12d2449f89" BLOCK_SIZE="4096" TYPE="ext4"
```

Edit fstab: 
 * The file **/etc/fstab** tells Linux : 👉 “Mount this disk automatically when the system starts”
```hcl
sudo nano /etc/fstab
```
Add :
```hcl
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
```hcl
sudo mount -a
```
  * 👉 No output = `everything correct`
  * 👉 Any error = `fix before reboot`

### 🔄 Reboot
```yaml
sudo reboot
```
### 🔍 Verify after reboot
```hcl
df -h
```
 * You should still see: `/data   mounted ✅`

---

## 🧠 Summary
  - EBS = Persistent, scalable block storage
  - Supports `snapshots`, `encryption`, and `resizing`
  - Multiple volume types for different workloads
  - Essential for production systems on AWS

✨ **Tip:** Use `gp3` for most workloads, `io2` for critical systems, and `sc1` for cheap storage.

---

## ⚡ AWS EBS (Elastic Block Store) — Rapid Fire Interview Q&A

| #️⃣ | ❓ Question                               | ✅ Answer                                                                                     |
| --- | ---------------------------------------- | -------------------------------------------------------------------------------------------- |
| 1️⃣ | 💾 What is Amazon EBS?                   | 👉 Amazon Elastic Block Store (EBS) is a persistent block storage service for EC2 instances. |
| 2️⃣ | 🏗️ What type of storage is EBS?         | 👉 Block Storage  (Block storage is a data storage method that divides files into identically sized pieces called "blocks".)     |
| 3️⃣ | ☁️ Which AWS service primarily uses EBS? | 👉 EC2                                                                                       |
| 4️⃣ | 🎯 Main purpose of EBS?                  | 👉 Persistent storage for operating systems, databases, and applications.                    |
| 5️⃣ | 🔄 Is EBS persistent?                    | 👉 ✅ Yes                                                                                     |
| 6️⃣ | ❌ Does EBS survive EC2 reboot?           | 👉 ✅ Yes                                                                                     |
| 7️⃣ | 🌍 Is EBS regional or AZ-specific?       | 👉 Availability Zone specific                                                                |
| 8️⃣ | 📦 What is an EBS Volume?                | 👉 Virtual hard disk attached to EC2 instances.                                              |
| 9️⃣ | 🛡️ Is EBS automatically replicated?     | 👉 Yes, within the same Availability Zone.                                                   |
| 🔟  | 🔌 Can EBS exist without EC2?            | 👉 ✅ Yes, as a detached volume.                                                              |


| #️⃣    | ❓ Question                                  | ✅ Answer       |
| ------ | ------------------------------------------- | -------------- |
| 1️⃣1️⃣ | 📊 Main EBS volume categories?              | 👉 SSD and HDD |
| 1️⃣2️⃣ | ⚡ General Purpose SSD volume?               | 👉 gp3         |
| 1️⃣3️⃣ | 📈 Previous generation SSD volume?          | 👉 gp2         |
| 1️⃣4️⃣ | 🚀 Highest performance EBS type?            | 👉 io2         |
| 1️⃣5️⃣ | 💽 Throughput-optimized HDD?                | 👉 st1         |
| 1️⃣6️⃣ | 🗄️ Cold HDD volume type?                   | 👉 sc1         |
| 1️⃣7️⃣ | 🏆 Recommended volume for most workloads?   | 👉 gp3         |
| 1️⃣8️⃣ | 📊 Best volume for databases?               | 👉 io2         |
| 1️⃣9️⃣ | 🎬 Best volume for big data/log processing? | 👉 st1         |
| 2️⃣0️⃣ | 📦 Best volume for archive workloads?       | 👉 sc1         |


## Scenario-Based EBS Q&A
| #️⃣    | 🚨 Scenario                           | ✅ Answer                                                      |
| ------ | ------------------------------------- | ------------------------------------------------------------- |
| 5️⃣9️⃣ | EC2 suddenly slow                     | 👉 Check EBS volume type, IOPS, throughput, QueueLength.      |
| 6️⃣0️⃣ | Root disk 100% full                   | 👉 Clean files, extend EBS volume, resize filesystem.         |
| 6️⃣1️⃣ | Expanded volume but OS shows old size | 👉 Filesystem not resized.                                    |
| 6️⃣2️⃣ | New volume attached but not visible   | 👉 Check `lsblk` and `fdisk -l`.                              |
| 6️⃣3️⃣ | Mount fails after attaching volume    | 👉 Filesystem missing or wrong device name.                   |
| 6️⃣4️⃣ | EC2 accidentally deleted              | 👉 Restore EBS snapshot and create new volume.                |
| 6️⃣5️⃣ | Need DR in another AZ                 | 👉 Create snapshot and restore volume in target AZ.           |
| 6️⃣6️⃣ | Database latency issue                | 👉 Use io2 volume.                                            |
| 6️⃣7️⃣ | Multiple servers need same volume     | 👉 Use Multi-Attach (io2/io1).                                |
| 6️⃣8️⃣ | Root volume deleted                   | 👉 Instance becomes unusable.                                 |
| 6️⃣9️⃣ | Security team requires encryption     | 👉 Enable EBS encryption with KMS.                            |
| 7️⃣0️⃣ | EBS bill increasing                   | 👉 Check unused volumes, snapshots, and overprovisioned IOPS. |
| 7️⃣1️⃣ | Volume stuck in optimizing state      | 👉 Normal behavior; volume remains usable.                    |
| 7️⃣2️⃣ | Application slow after migration      | 👉 Verify filesystem expansion and volume type.               |
| 7️⃣3️⃣ | EKS PVC stuck Pending                 | 👉 Check StorageClass, CSI driver, AZ mismatch.               |
| 7️⃣4️⃣ | Data lost after EC2 termination       | 👉 Volume deleted on termination or no backup.                |
| 7️⃣5️⃣ | Need 50,000 IOPS database storage     | 👉 Use io2.                                                   |

| #️⃣    | ❓ Question                                           | ✅ Answer                                                             |
| ------ | ---------------------------------------------------- | -------------------------------------------------------------------- |
| 4️⃣1️⃣ | 📈 Can EBS volumes be resized?                       | 👉 ✅ Yes                                                             |
| 4️⃣2️⃣ | ⚡ Can resize happen online?                          | 👉 ✅ Yes                                                             |
| 4️⃣3️⃣ | 🔄 What must be done after volume expansion?         | 👉 Resize filesystem.                                                |
| 4️⃣4️⃣ | 🔌 Can multiple volumes attach to one EC2?           | 👉 ✅ Yes                                                             |
| 4️⃣5️⃣ | 🖥️ Can one volume attach to multiple EC2 instances? | 👉 Only with Multi-Attach (io1/io2).                                 |
| 4️⃣6️⃣ | 📊 What is Multi-Attach?                             | 👉 One EBS volume attached to multiple EC2 instances simultaneously. |
| 4️⃣7️⃣ | 🌍 Can EBS move between AZs directly?                | 👉 ❌ No                                                              |
| 4️⃣8️⃣ | 🔄 How move volume to another AZ?                    | 👉 Snapshot → Create new volume in target AZ.                        |
| 4️⃣9️⃣ | 📎 Linux command to view disks?                      | 👉 `lsblk`                                                           |
| 5️⃣0️⃣ | 💽 Linux command to view partitions?                 | 👉 `fdisk -l`                                                        |

| #️⃣    | ❓ Question                                 | ✅ Answer                                  |
| ------ | ------------------------------------------ | ----------------------------------------- |
| 2️⃣6️⃣ | 📸 What is an EBS Snapshot?                | 👉 Point-in-time backup of an EBS volume. |
| 2️⃣7️⃣ | ☁️ Where are snapshots stored?             | 👉 Amazon S3 (managed internally by AWS). |
| 2️⃣8️⃣ | 🔄 Are snapshots incremental?              | 👉 ✅ Yes                                  |
| 2️⃣9️⃣ | 💰 Why are incremental snapshots useful?   | 👉 Lower storage cost.                    |
| 3️⃣0️⃣ | 🔁 Can you create a volume from snapshot?  | 👉 ✅ Yes                                  |
| 3️⃣1️⃣ | 🌍 Can snapshots be copied across regions? | 👉 ✅ Yes                                  |
| 3️⃣2️⃣ | 🛡️ Why take snapshots?                    | 👉 Backup and disaster recovery.          |
| 3️⃣3️⃣ | ⚡ Snapshot impact on production?           | 👉 Minimal impact.                        |
| 3️⃣4️⃣ | 🔐 Can snapshots be encrypted?             | 👉 ✅ Yes                                  |
| 3️⃣5️⃣ | 📦 Can AMIs use EBS snapshots?             | 👉 ✅ Yes                                  |

| ❓ Question                         | ✅ Strong Interview Answer                                                                             |
| ---------------------------------- | ----------------------------------------------------------------------------------------------------- |
| 💾 What is EBS?                    | 👉 "EBS is AWS's persistent block storage service used primarily with EC2 instances."                 |
| ⚡ gp3 vs gp2?                      | 👉 "gp3 provides independent IOPS and throughput configuration with better cost efficiency than gp2." |
| 📸 Why use snapshots?              | 👉 "Snapshots provide incremental backups for disaster recovery and migration."                       |
| 🔐 How secure EBS?                 | 👉 "Use KMS encryption, IAM policies, snapshots, and least-privilege access."                         |
| 🌍 Can EBS be attached across AZs? | 👉 "No. EBS volumes are AZ-specific; snapshots are used to move data between AZs."                    |

