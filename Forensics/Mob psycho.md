# **Mob Psycho**

## **Problem**
Can you handle APKs?

## **Solution**
Download the apk. Extract the files. 
Open a terminal from the new folder.
I used an educated guess...previous flags have been listed as "flag.txt"
So I ran the find function and it popped up. change directory and cat the file

└─$ find -name flag.txt
./res/color/flag.txt
                                                                                      
┌──(mdaleyjr㉿MLDKali)-[~/Downloads/PicoCTF]
└─$ cd ./res/color                      
                                                                                      
┌──(mdaleyjr㉿MLDKali)-[~/Downloads/PicoCTF/res/color]
└─$ cat flag.txt  
7069636f4354467b6178386d433052553676655f4e5838356c346178386d436c5f62313132616535377d


Decode that hash for the flag: picoCTF{ax8mC0RU6ve_NX85l4ax8mCl_b112ae57}
