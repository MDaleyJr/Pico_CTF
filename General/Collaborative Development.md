# **Collaborative Development**

## **Problem**
My team has been working very hard on new features for our flag printing program! I wonder how they'll work together?

## **Solution**
Download the zip and extract it. Open a terminal in the new extracted folder:
git log

└─$ git log         
commit d7d09540eb1a24ed1299b230d143e6e93f9807eb (HEAD -> main)
Author: picoCTF <ops@picoctf.com>
Date:   Tue Mar 12 00:07:52 2024 +0000

    init flag printer

now run branch -a to see if there are any branches
└─$ git branch -a
  feature/part-1
  feature/part-2
  feature/part-3
* main

Now we can run the git checkout toget into each branch and cat the file 

└─$ git checkout feature/part-1
Switched to branch 'feature/part-1'
                                                                                      
┌──[~/Downloads/PicoCTF/drop-in]
└─$ cat flag.py       
print("Printing the flag...")
print("picoCTF{t3@mw0rk_", end='')                                                                                      
┌──-[~/Downloads/PicoCTF/drop-in]
└─$ git checkout feature/part-2
Switched to branch 'feature/part-2'
                                                                                      
┌─-[~/Downloads/PicoCTF/drop-in]
└─$ cat flag.py
print("Printing the flag...")

print("m@k3s_th3_dr3@m_", end='')                                                                                      
┌──-[~/Downloads/PicoCTF/drop-in]
└─$ git checkout feature/part-3
Switched to branch 'feature/part-3'
                                                                                      
┌──-[~/Downloads/PicoCTF/drop-in]
└─$ cat flag.py
print("Printing the flag...")

print("w0rk_7ae8dd33}")

piece all 3 parts together picoCTF{t3@mw0rk_m@k3s_th3_dr3@m_w0rk_7ae8dd33}
