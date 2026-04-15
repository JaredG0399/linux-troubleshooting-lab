# 33 - Permission Denied (File Exists)

##Scenario:
- A user reported that they could see a file but were unable to open it, receiving a "permission denied" error.

##Investigation:
- The file permission were checked: "ls -l /var/www/html/file.txt
- The output showed: -rw------ 1 root root file.txt

##Analysis:
- The file existed, but permissions were restricted: 
	-Only the owner (root) had read and write access
	-Group and others had no permissions
- This prevented other users from accessing the file.

##Root cause:
- The file permissions were to restrictive, allowing access only to the root user.

##Resolution:
- Permissions were modified to allow read access: "sudo chmod 644 file.txt"
- This granted:
	-Owner: read and write
	-Group: read
	-Others: read

##Verification:
- The permission were verified: "ls -l /var/www/html/file.txt
- The output showed: " -r-r--r-- 1 root root file.txt
- The user was then able to access to file successfully.

##Security consideration:
- chmod 644 allows all users to read the file. THis is appropriate for public content such as web files.
- For sensitive files, a more restrictive permission such as 640 should be used.

##Conclusion:
- Permission issues can prevent access even when files exist. Understanding file permissions and ownership is essential for troubleshooting access problems.

##Commands used:
- ls -l /var/www/html/file.txt
- sudo chmod 640 file.txt
