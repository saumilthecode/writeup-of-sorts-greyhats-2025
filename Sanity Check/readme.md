# ⚠️ Warning, this is the hardest challenge in the ENTIRETY of this CTF some terms i may use in this writeup may be unfamiliar ⚠️
key thinking ideas: #ceasire shaft

So firstly, what is Sanity Check?

Well on first glance it seems like its a invitiation as it reads

>  Welcome to GreyCTF Qualifiers 2025!
> 
> This is a simple sanity check to ensure everything is working: your setup, your submissions, and your sanity.
> 
> If you're seeing this challenge, congrats — you're all set to begin.
> 
> Submit the flag to get started: grey{w3lc0m3_2_gr3yctf_2025_fabb13becc1}

Ah such a deceptively simple chalenge? Well it must truely be something much more demanding!

![](https://github.com/saumilthecode/writeup-of-sorts-greyhats-2025/blob/main/Sanity%20Check/im_not_sane.jpeg?raw=true)

Ok so the first thing to do is use the Caesar Cipher website and run the entire chal description through

After shifting it 🠞3 (🠜23)	 (i dont know what those characters are either)

we end up with 

> Tbizljb ql DobvZQC Nrxifcfbop 9792!
> 
> Qefp fp x pfjmib pxkfqv zebzh ql bkprob bsbovqefkd fp tlohfkd: vlro pbqrm, vlro pryjfppflkp, xka vlro pxkfqv.
> 
> Fc vlr'ob pbbfkd qefp zexiibkdb, zlkdoxqp -- vlr'ob xii pbq ql ybdfk.
> 
> Pryjfq qeb cixd ql dbq pqxoqba: dobv{t0iz7j0_9_do0vzqc_9792_cxyy80ybzz8}

So we must clearly be dealing with some form of manipulation as there is a flag!

So lets feed it to chatgpt and see what it says!
![](https://github.com/saumilthecode/writeup-of-sorts-greyhats-2025/blob/main/Sanity%20Check/SCR-20250604-iplc.png?raw=true)

Ahaha! the flag albsy{q0fw7g0_9_al0synd_9792_zvww80vyww8}

![](https://github.com/saumilthecode/writeup-of-sorts-greyhats-2025/blob/main/Sanity%20Check/SCR-20250604-iqnp.png?raw=true)

and its probhably correct since the ctf platform says You already solved this :D
![](https://github.com/saumilthecode/writeup-of-sorts-greyhats-2025/blob/main/Sanity%20Check/download.jpeg?raw=true)

