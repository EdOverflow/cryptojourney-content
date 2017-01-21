# Cryptojourney

Written by @EdOverflow & @YouPunk.

# Table of contents

- [1. Foundations](#1-foundations)
- [2. Classical Cryptography](#2-classical-cryptography)
- [3. WWI](#3-wwi)
- [4. WWII](#4-wwii)
- [5. Cold War](#5-cold-war)
- [6. Modern-day Cryptography](#6-modern-day-cryptography)

# 1. Foundations

# 2. Classical Cryptography

### Rome

One of the earliest known and simplest ciphers, the Caesar cipher, is a shift cipher, which means it encrypts by shifting all the letters in a piece of text by a certain number of places. It was named after Julius Caesar, who used it to encrypt messages sent to his generals. Caesar ciphers are very simple to create, but are also very easy to crack. The key for this cipher is a letter which represents the number of shifts in the alphabet. So for example, a key of E means "shift 4 places". The key Z can either mean "shift 25 places" or "shift one place backwards".

#### 🎓 Example

The word "HELP" with the key J becomes "ROVZ".

~~~~
ABCDEFGHIJKLMNOPQRSTUVWXYZ
KLMNOPQRSTUVWXYZABCDEFGHIJ
~~~~

Caesar's method is a weak encryption method, since there are only 26 possibilities. The Enigma machine used in World War II by the German military had over 158 quintillion combinations! To crack the Caesar cipher we can also use a method called frequency analysis. This is where the number of times each letter occurs is analysed. The frequency of the most commonly occurring letters in the cipher text correspond to the most common in the plaintext (etaoin shrdlu).

#### 🎓 Example

The following cipher text is given:

~~~~
RYYVBGWHFGNGRPU
~~~~

After analysing the text we get:

| Letter | Percentage | Number of occurrences |
|--------|------------|-----------------------|
| N      | 6.67%      | 1                     |   
| P      | 6.67%      | 1                     |   
| U      | 6.67%      | 1                     |   
| F      | 6.67%      | 1                     |   
| W      | 6.67%      | 1                     |   
| V      | 6.67%      | 1                     |   
| B      | 6.67%      | 1                     |   
| H      | 6.67%      | 1                     |   
| R      | 13.33%     | 2                     |   
| Y      | 13.33%     | 2                     |   
| G      | 20.0%      | 3                     |  

Now we compare the most common letters from the cipher text with the most common English letters: etaoin shrdlu

~~~~
If cipher text `G` is plaintext `E`, then the shift is `2`.
Result: pwwtzeufdelepns
Else if cipher text `G` is plaintext `T`, then the shift is `13`.
Result: elliotjustatech
~~~~

#### :hourglass: Challenge

It is believed that Julius Caesar used a key of E when encrypting messages. Try to decrypt this message Caesar sent to one of his generals.

<details>
  <summary>**M leh vexliv fi jmvwx mr e zmppeki xler wigsrh ex Vsqi.**</summary>
	**Solution:** I had rather be first in a village than second at Rome.
</details>

# 3. WWI

# 4. WWII

### The Enigma Machine

![](img/enigma-k.jpg)

Enigma machines were a series of rotor cipher machines, originally used by companies, banks and later by the German military during WWII to encrypt messages. The main difference to classical cryptographic methods, was the fact that the cipher was polyalphabetic. The key changed for each individual letter you enciphered. So for example, you might press a `J` and end up with an `E` the first time and a `B` the second time.

The early Enigma machine consisted of a keyboard, a lampboard and three rotors with 26 letters each. When a key was pressed a letter flashed on the lampboard and the right rotor turned one step. Once the right rotor had made one full revolution, it kicked the middle rotor by one step and so forth, just like an [odometer](https://upload.wikimedia.org/wikipedia/commons/thumb/0/0b/Odometer_70000.jpg/800px-Odometer_70000.jpg). So if you set the rotors to A-B-C, the following would happen:

~~~
A-B-C -> A-B-D ... A-B-Z -> A-C-A
~~~

![Parts of the Enigma machine](img/enigma_a.jpg)

When the German military saw the potential of the machine, they used various methods to insure better security. First they increased the number of rotors to four `4 * 3 * 2 = 24 permutations`. They then added a plugboard, which paired letters together with 10 wires `26! / (6! * 10! * 2^10) = 150'738'274'937'250 permutations`.

~~~
Total combinations: 1054560 * 150,738,274,937,250 = 158,962,555,217,826,360,000 ≈ 1.59 * 10^20
~~~

![Enigma plugboard](img/plugboard.jpg)

So now that we know the different parts of an Enigma machine, lets have a look at how to set up the machine to encrypt and decrypt a message:

**The rotor order:** Numbered from one to three in Roman numerals (I-III), each rotor was wired up differently and when placed on the rack in different order, they gave a different output.

![Eingma rotor](img/enigma_rotor.jpg)

**The ring setting:** The numbers displayed through little holes next to the rotors, indicated the ring setting. Each rotor was assigned a ring setting.

**The ground setting:** The key.

![Enigma ground setting](img/enigma_b.jpg)

**Plugging:** Two letters could be connected together with a wire.

**The reflector wheel:** The circuit passed through the rotors and was then reflected back through the three rotors.

#### 🎓 Example

You have got hold of an Enigma machine and a stolen list for this month. The list says the following:

~~~
Datum (date DD/MM/YY):              04/09/1939
Walzenlage (rotor order):           | I  | II | III |
Ringstellung (ring setting):        | 12 | 25 |  01 |
Steckerverbindungen (plug setting): AF DU LQ VZ PI WX HM OF GD SC
Kenngruppen (identification group): LOL
~~~

1. This means you must set rotor `I` to 12, rotor `II` to position 25 and rotor `III` to 1.

2. Next you place rotor `I` in the left slot, rotor `II` in the middle slot and rotor `III` in the right slot. Rotor `III` will spin the fastest.

3. Now that all of that is done, you must connect all the pairs listed above together. `A` with `F`, `D` with `U` and so on.

The following steps were taken to ensure that both ends could communicate:

1. Both sender and recipient had to have the same machine, or at least both machines had to be configured so as to be in the same state. This means the same reflector wheel, rotor order, ring setting and ground setting were used to encrypt and decrypt the message.

2. Everyday these settings changed and so German operators were handed out keylists of all the different settings for the month. If the enemy got hold of a list, which they did sometimes, the list became useless once the month was over. Obviously, if there was any suspicion of a missing keylist, the Germans would have generated a new one. Keylists were either distributed in printed form or over radio as Morse code. The German Navy used ink that disappeared in water, so that when a ship sank the keylist was destroyed.

![Enigma keylist](img/enigma_keylist.jpg)

Now if both ends have followed all these steps accordingly, the sender could encrypt `HELLO` with his machine, which might output something like `UZCFS`. The receiver can then type `UZCFS` into his machine and it should output `HELLO`.

---

### The Bombe

The Bombe was a device used by the British cryptologists at Bletchley Park to decode German Enigma messages during WWII. The Bombe was designed in 1939 at the UK Government Code and Cypher School (GC&CS), a peace-time codebreaking agency, by Alan Turing and Gordon Welchman.
In order to decrypt Enigma messages the Bombe had to find out the relative starting positions of the Enigma rotors, the cross-pluggings of the Enigma plugboard and the order of the rotors. The Bombe could not solve everything on its own, therefore some work had to be done by the codebreakers manually. For instance likely pieces of plain-text known as Cribs had to be found by the codebreakers and then inserted into the Bombe machine.

#### Roll of Drums

The Bombe had to do one thing, it had to replicate the action of several Enigma machines. A standard British Bombe replicated the actions of 36 Enigma machines wired together, each with 3 drums connected to them to produce the same effect as the Enigma rotors. To recreate the Enigma rotors actions, each rotor drum of the Bombe had two sets of contact and 104 wire brushes that were arranged in four circles, 2 input and 2 output circles. The circles were arranged, so that the 2 output circles were connected with the current passing through the rotors, and the 2 input circles were connected with the current passing in the other direction.

---

### Lorenz Cipher

Another cipher machine, which the German military used towards the end of WWII is the Lorenz machine. The Lorenz machine was a rotor stream cipher machine often used by Nazi High Command and famously known to have been Adolf Hitler's cipher of choice. Lorenz machines were attached to teleprinters, in order to encrypt important messages. Each machine model starts with an SZ abbreviation (SZ-40, SZ-42, etc.), which stands for "Schlüssel-Zusatz", the German for "cipher attachment".

![](img/lorenz.jpg)

#### :radio: The Machine

The Lorenz cipher machine, although not as famous as Enigma, was far more complex than Enigma. Lorenz machines had 12 rotor wheels and each wheel had a different number of pins, which could be set to on or off. The rotor wheels were divided into 3 groups, `χ` ("chi"), `ψ` ("psi") and `μ` ("mu"). `χ` and `ψ` wheels are key wheels and by adding both together they output a key.

~~~
Key = χ-Key + ψ-Key
~~~

![](img/lorenz_rotor_wheels.jpg)

`χ` wheels rotate after every letter that is typed, while `ψ` wheels do not change regularly. The two middle `μ` wheels are responsible for the rotation of the `χ` and `ψ` wheels, and are therefore called motor wheels.

| Rotor number:  |1  |2  |3  |4  |5  |6  |7  |8  |9  |10 |11 |12 |
|----------------|---|---|---|---|---|---|---|---|---|---|---|---|
|Type:           | ψ | ψ | ψ | ψ | ψ | μ | μ | χ | χ | χ | χ | χ |
|Number of pins: |43 |47 |51 |53 |59 |37 |61 |41 |31 |29 |26 |23 |

Lorenz machines used an enciphering method proposed by the American scientist, Gilbert Vernam, to encrypt teleprinter messages. Letters were represented as dots ("•") and crosses ("x") and in order to encrypt the message, the typed letter was XOR'd with the key letter. The XOR of `(•,•)` is `•`; `(•,x)` is `x`; `(x,•)` is `x`; and `(x,x)` is `•`.

~~~
Letter A: x x • • •
   Key C: • x x x •
------------------- (XOR)
Cipher F: x • x x •
~~~

---

### Bletchley Park

Bletchley Park was the home of the British Codebreakers during World War II, and was run by the Government Code and Cypher School (GC&CS). The park is located in Buckinghamshire, England. The advantage of the parks location was its centrality. It was just in the middle of the Oxford and Cambridge universities who supplied many code-breakers. Bletchley Park is famous for cracking naval Enigma and Lorenz codes. Although many incredible minds worked together to decode messages at Bletchley, the most famous codebreaker remains Alan Turing. In 1945 Bletchley Park had about 10‘000 code-breakers at their service, 75% of them were women, due to the lack of men, who had been sent to war. The extreme secrecy around Bletchley Park meant that many of the achievements were not revealed until decades later. All staff members had to sign the Official Secrets Act to ensure their loyalty. They were told not to talk about Britain’s "Ultra secret" or any of the intelligence acquired by decrypting enemy messages and signals. Members were not even allowed to share this information with their relatives or discuss it at Bletchley Park. This discretion was partially respected, since Germany had no idea about Britain’s success, even though we know today, that Bletchley Park had been infiltrated by a Soviet spy that leaked information about the "Ultra secret". Today, Bletchley Park is a famous tourist attraction.

#### :hourglass: Challenge

<details>
  <summary>Why is it important that codebreaking agencies are hidden and operated in secret?</summary>
	**Solution**: If enemies were to find out about a codebreaking agency, they could send spies, improve their encryption methods and possibly send fake messages to put off the enemy.
</details>

# 5. Cold War

# 6. Modern-day Cryptography