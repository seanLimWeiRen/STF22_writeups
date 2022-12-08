# Stack The Flags 2022: BlogPost

![Contest Date: 02.12.2022](https://img.shields.io/badge/Contest%20Date-02.12.2022-lightgrey.svg)
![Solve Moment: During The Contest](https://img.shields.io/badge/Solve%20Moment-During%20The%20Contest-brightgreen.svg)
![Difficulty: Easy](https://img.shields.io/badge/Difficulty-Easy-brightgreen)

## Description

> Jaga created an internal social media platform for the company, can you leak anyone's information?



## Attached Files

- [Source code](https://github.com/seanLimWeiRen/STF22_writeups/tree/main/Web/BlogPost/attached_files)

## Summary

We use XSS to steal the admin's cookies

## Flag

```
STF22{s1mpl3_p0st_xSs_:)}
```

## Detailed Solution

Upon visiting the website and clicking one "Login", we are greeted with a login page which gives us a link to register an account.

![1.png](images/1.png)

After registering an account and logging in with it, we can see that an admin has created a post, providing us with the information that there is an admin account and we might need to gain access to it.

![2.png](images/2.png)

```
STF22{s1mpl3_p0st_xSs_:)}
```
