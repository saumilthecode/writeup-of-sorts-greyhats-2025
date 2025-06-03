# Red Flag Recon

chal :
> Since announcing GreyCTF, we've noticed persistent comments on the GreyHats Instagram account from a user keen to create a challenge for us. But with GreyCTF so close to our final exams, we haven't had the bandwidth to properly vet him. Help us check him out, make sure there are no red flags.

>Note: There is only one flag in this challenge. If it fits the flag format grey{...}, you've likely got it!

So cutting to the chase, you'd need to first start by checking the GreyCTF instagram where clicking on the first post results in this comment from ``ducati777__``

![](https://github.com/saumilthecode/writeup-of-sorts-greyhats-2025/blob/main/Red%20Flag%20Recon/SCR-20250603-jvln.jpeg?raw=true)

follow the `ducati777__` leads to this

![](https://github.com/saumilthecode/writeup-of-sorts-greyhats-2025/blob/main/Red%20Flag%20Recon/SCR-20250603-jwav.png?raw=true)

Clealry the author wants us to check out the twitter which is x.com/ducati777_

![](https://github.com/saumilthecode/writeup-of-sorts-greyhats-2025/blob/main/Red%20Flag%20Recon/SCR-20250603-jwjs.png?raw=true)

as visible from the ctf style "flag" in his bio hes clerly related and not some random dude on tiktok who shares the same handle (sherlock lead me to it dont ask why i even bothered)

![](https://raw.githubusercontent.com/saumilthecode/writeup-of-sorts-greyhats-2025/refs/heads/main/Red%20Flag%20Recon/Screenshot_20250601_123351.webp)

so following back on the twitter, theres not much of interest other then a mentioned github repo which persumably has the key.

So the only lead is to follow this picture of the github repo where the commit hash is visible. And as we all know, COMMIT HASES ARE UNIQUE NO TWO HASHES ARE THE SAME!!!!!!
(image related to github)
![](https://github.com/saumilthecode/writeup-of-sorts-greyhats-2025/blob/main/Red%20Flag%20Recon/1733953236922.jpeg?raw=true)

so following the picture (attached)
![](https://pbs.twimg.com/media/GpXtG9UbYAAkAPm?format=jpg&name=4096x4096)

Shows the hash `dc3b9d7`

Putting this hash into github leads to the exact commit which he showed in the picture 

![](https://github.com/saumilthecode/writeup-of-sorts-greyhats-2025/blob/main/Red%20Flag%20Recon/SCR-20250603-jyjr.png?raw=true)
 
so the flag is somewhere inside [here](https://github.com/Brainstorm-Nonsense/chal-collection/commit/dc3b9d7de40686b9895438e80ae4912a0682d387)

so after locally cloning it and using GitKraken to look through it, i realised theres batshit

![](https://github.com/saumilthecode/writeup-of-sorts-greyhats-2025/blob/main/Red%20Flag%20Recon/SCR-20250603-jzrh.png?raw=true)

this bugger clearly has better cybersecurity then a gopher. 

So going back to the twitter post, he mentioned something about a private fork.

after consulting chatgpt i got absolutely bamboozled and didnt figure it out

So after the fact that the org writeups dropped, we were supposed to use TruffleHog to find hidden hashes which i stil cant figure out how to use trufflehog so if anyone finds out lmk on discord @im_too_sad_to_think_of_anything

but im stil hoping the first part of my solve by using the hash was unique enough to get moolah <3