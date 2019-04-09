# Password-Cracker
Program by Sang Mai, Zyra De Los Reyes and Paul Ries

Overview:
In this project you will be both saving and storing passwords, as well as trying to “crack” a
password file. This project is divided up into two parts. This project will require the use of a
cryptographic library to do hashes. That information is linked at the end.
While you can do this project by yourself, I will allow you to work in pairs, as this project tends
to have a fairly straightforward division of labor for at least part of the project. Note that these
parts might not be equally difficult and certainly you will have to come to some agreement on
format and encoding before starting, so do not assume you will be able to code your part without
input from the other.

Task 1:
Write a program that allows a user to create an account and then authenticate whether or not they
have an account. However, the trick is that this is done through three different password files. So
when the program starts, it should ask the user which one of those they should like to either log
in or authenticate through. Once they have done that, your program will ask them if they want to
make an account or log in. If they want to log in, your program should accept their username and
password and verify that using the appropriate password file. If they want to create an account,
the program should create the appropriate data in the appropriate password file. Note the primary
purpose of this program is to allow testing of parts 2 and 3.
For ease of cracking later, I want your passwords to be restricted to only lowercase letters (a..z)
of configurable length. The length of the salt should be one byte.
Usernames should be restricted to 8 alphanumeric characters.
The three password files should be as follows:
1) A plaintext username password pair, stored in text in a file
2) A username and a hashed password, stored in some format in the file
3) A username, a salt and a hashed password+salt, stored in some format in the file

Task 2:
Write a program that, when given bounds on password size (for example, all passwords between
length 3 and 8) and a number of accounts (100 for example), will then create random usernames
and passwords in the specified ranges and then create 100 accounts for each of the 3 password
files. 

Task3:
 In this task we will be attempting to crack one of the password files. You can assume that you
have full knowledge of the format of the particular file you are working with. This program
should take as an option one of the password files above (only 2 or 3, 1 is trivial), as well as a
maximum password size. It should then try to figure out one of the passwords in that file by
brute force. That is, if ran with a password file of type2, it would attempt to find a password that
hashed to one of the passwords of a username in the file, trying all combinations of passwords up
to some specified length. If called with a password file of type3, it would attempt to find a
password that when hashed with the salt would match one of the usernames.
Note that trying to crack a file of type 2, you can compare your hash against all of the usernames
in the file. This you can do by loading this file into some structure. As you are searching for a
particular match, this is done much more efficiently if it is stored in a binary search tree or
similar structure. For files of type 3, whether your need to do something like this or not is
something I leave up to you to consider.
Testing and Analysis:
You now have a program that creates password files, one that can test some of those passwords
and a program that is supposed to try and crack some of those passwords.
For the final part of this project, I want you to experiment and find for me how long it takes your
password cracker to crack one of the passwords in the files using type 2 and type 3 for various
bounds of random files (ex: file of 1000 passwords of length 3 to 8). I want you to be able to
describe to me which format is more secure and give some concrete numbers on how much more
secure it is. I would like you to tell me what password length would be the minimum to be secure
on the system that you ran the code on. Be ready with some conclusions, though more
importantly the ability to talk about what you discovered or had problems with.

Cryptographic library:
For this project you will need some cryptographic library that lets you do hashes. You can pick
an environment to do this in, but as all of us have access to the delmar, if you do not have a
better idea I would suggest to use the OpenSSL library.
https://www.openssl.org/
You will then need to install it (locally) from source on delmar,
https://wiki.openssl.org/index.php/Compilation_and_Installation
The openssl files themselves are available through that link but also at
/accounts/facstaff/hauschildm/Crypto 

Then you have to compile it, so you do:
make
Then you have to install it:
make install
You should then test the environment by writing a program that does some basic operation. I
have example code to do this on delmar, located at
/accounts/facstaff/hauschildm/Crypto/proj2test
which has a Makefile and some source files for a program that takes in a string from the user and
hashes it in C.
