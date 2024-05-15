# **Commitment Issues**

## **Problem**
I accidentally wrote the flag down. Good thing I deleted it!

## **Solution**
Download the zip
Extract the data
Open terminal from the extracted folder
git log (data pops up with users hash)

└─$ git log         
commit ef0b7cc6b98367fa168573c931e0f7098ef59182 (HEAD -> master)
Author: picoCTF <ops@picoctf.com>
Date:   Tue Mar 12 00:06:20 2024 +0000

    remove sensitive info

commit ea859bf3b5d94ee74ce5ee1afa3edd7d4d6b35f0
Author: picoCTF <ops@picoctf.com>
Date:   Tue Mar 12 00:06:20 2024 +0000

    create flag


then run get show using the hash
└─$ git show ef0b7cc6b98367fa168573c931e0f7098ef59182
commit ef0b7cc6b98367fa168573c931e0f7098ef59182 (HEAD -> master)
Author: picoCTF <ops@picoctf.com>
