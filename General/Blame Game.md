# **Blame Game**

## **Problem**
Someone's commits seems to be preventing the program from working. Who is it?

## **Solution**
Download the zip and extract it. Open a terminal from the new extracted folder:
do a git log

─$ git log
commit b7f1fb20f72e493f604ccb3b9f2639a00c566939 (HEAD -> master)
Author: picoCTF <ops@picoctf.com>
Date:   Tue Mar 12 00:07:08 2024 +0000

    important business work

commit c16a2576a68c7166d13f3e877ea4b4cfc675d343
Author: picoCTF <ops@picoctf.com>
Date:   Tue Mar 12 00:07:08 2024 +0000

    important business work


the list of entries was ridiculously long....but author was the same for as long as I looked.
There might not be too many Authors and thats all we need. so add grep authors to the function and look for
someone new

└─$ git log | grep Author 
Author: picoCTF <ops@picoctf.com>
Author: picoCTF <ops@picoctf.com>
Author: picoCTF <ops@picoctf.com>
Author: picoCTF <ops@picoctf.com>
Author: picoCTF <ops@picoctf.com>
Author: picoCTF{@sk_th3_1nt3rn_cfca95b2} <ops@picoctf.com>
Author: picoCTF <ops@picoctf.com>

the intern was at the bottom but since only authors were listd and the intern was the only one different a fast
scroll was easy
