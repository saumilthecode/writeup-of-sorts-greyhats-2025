# Uwusignatures! [who came up with this name]

> As an uwu girl, I decided to make this digital signature scheme to share my signatures with everyone!
> I'll only show you half of my signature though, because I'm shy...

> Surely, no one would steal from a cutie like myself... right?

> nc challs.nusgreyhats.org 33301
> nc challs2.nusgreyhats.org 33301

ok so my first thought is who decided to come up with this ingenunious name lol


but anyways here's how to solve it.
i went about this using python to establish a connection with the server.

-------

**1. Connect to the Remote Server**
* The script connects to the remote challenge server using a TCP socket. It sets up a file-like interface to easily send and receive lines of text and JSON messages. This allows interaction with the server’s interface. I made a python programme to connect to this and to eventually obtain the flag.

**2. Receive Public Parameters**
* The server sends the public cryptographic parameters: p, g, y = g^x mod p, along with a leaked value `k`. Normally, `k` should remain secret, but its exposure creates a vulnerability. Now we use this secret `k` value to our advantage!

**3. Calculate `r`**
* Using the known value `k`, the script computes `r = g^k mod p`, which is part of the signature. This will be important for later.

**4. Request a Valid Signature**
* The script chooses option 2 from the server menu to request a signature on an arbitrary allowed message, such as `m = 42`. The server replies with the corresponding signature `s1`. This gives the attacker a valid `(m1, s1)` pair tied to the leaked `k`.

**5. Recover the Private Key and Forge Signature**
* With the known valuees `k`, `r`, and received `s1`, the script forms an equation involving the private key `x`. It solves the equation `r·x ≡ h1 − s1·k (mod p−1)` to compute `x`. Each candidate is checked until one satisfies `g^x ≡ y mod p`, confirming the correct private key. The forbidden message `"gib flag pls uwu"` is converted into an integer and hashed. Using the recovered `x` and known `k`, the script computes a valid signature `(r, s_flag)` for it. This signature mimics a genuine one, bypassing the restriction.

**6. Submit and obtain**
* Now for the best part, thef orged message and signature are submitted via the server’s menu under the “verify signature” option. The server processes this and checks the validity. When successful, it prints the flag in `grey{}` format.

And to conclude, the flag obtained is, `grey{h_h_H_h0wd_y0u_Do_tH4T_OMO}` 
* sounds funny lmaoooo
