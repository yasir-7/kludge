# Solutions

The steps below provide a detailed solution to the given problem. Tools used here are- aperisolve.com, strings, steghide, sha256, base64 encryption, Vigenère ciphers, Ghidra.

## Step 1

Use aperisolve.com and load the image or strings car.jpg in ubuntu terminal to extract all the strings from the image. You will recieve a string "does the password #kludge look simple?" .
From here we get to know that kludge is the password. Now it could have been a password with only alphabets but the string tells that the password might not be simple and yesit has '#' which has a 
significance here. As the password here is **SHA256** encryption of kludge which is "**72b159c96e2505ed949e545c78bae25d445d0483dfe8f892abba7bc26f062245**".

## Step 2

The above obtained password/passphrase is now used while extracting data from steghide to obtain a file a.out. This a.out file is generated on compiling a code which has numerous functions out of which two 
are of use namely **want_the_flag** and **here_it_is**. The above code can be analyzed using a decompiler such as ghidra. On analyzing the **main** function, We get a hint to go to the **want_the_flag** function
and then on getting further hint we reach the **here_it_is** function.

## Step 3

The **here_it_is** function contains few more hints and one can identify the **key** to be "**missing**" and that the text given in the function is encrypted using **Vigenère ciphers**. Then the encrypted string 
can be decoded by entering the given **key** and obtain another hint which says "**WHAT IS 2^6? IS IT a2x1ZGdlQ1RGe215X2NoNGxsZW5nZX0=**".

## Step 4

This text is another hint as it contains 2^6 which is 64 and can be used to decode the string "**a2x1ZGdlQ1RGe215X2NoNGxsZW5nZX0=**" using **base64 decryption**. The string would eventually evaluate to 
**kludgeCTF{my_ch4llenge}** which is the flag for the given problem.
