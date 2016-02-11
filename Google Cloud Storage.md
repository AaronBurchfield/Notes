## Using Google Cloud Storage as file storage from an Ubuntu server
### Create a bucket
1. From your Google Cloud project, browse to the **Storage** node.
2. Select **CREATE BUCKET** and provide a bucket name, storage class, and
 region.

### Interoperable storage access keys
Create access keys to connect to the storage backend.

1. From the Bucket browser, select Settings.
2. On the **Interoperability** tab, select **Create a new key**.
3. Note **Access key** and **Secret**.

# Enter s3ql
We'll use s3ql to mount the storage backend on our host.
S3ql will create an encrypted filesystem in the Google Cloud Storage bucket.
Once mounted we can place files in the s3ql filesystem by moving them to the
 mountpoint. We can also transfer files to the s3ql filesystem through the
 server with familiar tools like ```rsync``` or ```scp```. Files in the
 mountpoint will appear and function like any local file. Just keep in mind
 that Google Cloud Storage fees are applied not just on the amount of data in a
  bucket, but also by the number of requests.
### Install s3ql from the Ubuntu universe repo

    apt-get install -y s3ql

### Create s3ql authorization file
    vim ~/.s3ql/authinfo2

    [gs]
    storage-url: gs://your-bucket-name/
    backend-login: YOUR_ACCESS_KEY
    backend-password: YOUR_ACCESS_SECRET
    fs-passphrase: YOUR_FILESYSTEM_PASSPHRASE
### Mount the storage backend
Create a directory for the mountpoint and attach the storage backend.

    mkdir /mnt/mountpoint
    mount.s3ql gs://your-bucket-name /mnt/mountpoint

By default only the user who mounted the storage backend will be able to access
 the content.
To allow all users on a host access to the mounted bucket specify
 ```--allow-other``` when mounting.

### Other tips
#### Unmount the virtual file system

    unmount.s3ql gs://your-bucket-name

#### Repair the virtual file system

    fsck.s3ql gs://your-bucket-name
