# Tung Tung Tung Sahur

> New to the world of brainrot? Not sure what names to pick from? We've got you covered with a list of our faves:
> 
> Tralalero Tralala
> 
> Chef Crabracadabra
> 
> Boneca Ambalabu
> 
> Tung Tung Tung Tung Tung Tung Tung Tung Tung Sahur

As a very very interested brainrot connoisseur i am qiute in dept with the brainrot lore
(video related)
https://github.com/saumilthecode/writeup-of-sorts-greyhats-2025/blob/main/Tung%20Tung%20Tung%20Sahur/ScreenRecording_04-08-2025%2020-43-38_1.MP4
<video controls width="600">
  <source src="https://github.com/saumilthecode/writeup-of-sorts-greyhats-2025/raw/main/Tung%20Tung%20Tung%20Sahur/ScreenRecording_04-08-2025%2020-43-38_1.MP4?" type="video/mp4">
  Your browser does not support the video tag.
</video>

Ok so we are provided with a .txt and .py file

the txt is called output.txt and contains

```
~ truenciated ~

Tung!
Tung!
Tung!
Sahur!
e = 3
N = 140435453730354645791411355194663476189925572822633969369789174462118371271596760636019139860253031574578527741964265651042308868891445943157297334529542262978581980510561588647737777257782808189452048059686839526183098369088517967034275028064545393619471943508597642789736561111876518966375338087811587061841
C = 49352042282005059128581014505726171900605591297613623345867441621895112187636996726631442703018174634451487011943207283077132380966236199654225908444639768747819586037837300977718224328851698492514071424157020166404634418443047079321427635477610768472595631700807761956649004094995037741924081602353532946351

~ end ~
```

well that provides some sort of clue! Now on to the .py

```python
from Crypto.Util.number import getPrime, bytes_to_long

flag = "grey{flag_here}"

e = 3
p, q = getPrime(512), getPrime(512)
N = p * q 
m = bytes_to_long(flag.encode())
C = pow(m,e)

assert C < N 
while (C < N):
    C *= 2
    print("Tung!")

# now C >= N

while (C >= N):
    C -= N 
    print("Sahur!")


print(f"{e = }")
print(f"{N = }")
print(f"{C = }")
```

Ok so the number of Tung!'s and Sahur! and the long aah strings mean something!

So theres 164 Tung's and 1 Sahur

so to reverse the flag out of it, we need to 

```python
from sympy import integer_nthroot
from pathlib import Path

# Load and parse the output file
output_text = Path("output.txt").read_text()

# Count "Tung!" and "Sahur!" lines
tung_count = output_text.count("Tung!")
sahur_count = output_text.count("Sahur!")

# Extract e, N, C values from the bottom of the file
lines = output_text.strip().splitlines()
e = int(lines[-3].split(" = ")[1])
N = int(lines[-2].split(" = ")[1])
C = int(lines[-1].split(" = ")[1])

# Recover the original ciphertext before modification
C_original = (C + N * sahur_count) // (2 ** tung_count)

# Recover the original message by taking the e-th root
m, exact = integer_nthroot(C_original, e)

# Convert number back to bytes
try:
    flag = m.to_bytes((m.bit_length() + 7) // 8, "big").decode()
except UnicodeDecodeError:
    flag = "[Failed to decode flag]"

flag
```

and the flag is `grey{tUn9_t00nG_t0ONg_x7_th3n_s4hUr}`

tanks for reading!

![](https://raw.githubusercontent.com/saumilthecode/writeup-of-sorts-greyhats-2025/refs/heads/main/Idk/cat.webp)
