### The Enigma Machine

<span class="ipa center">/ɪˈnɪgmə/</span>

![](../img/enigma-k.jpg)

Enigma machines were a series of rotor cipher machines, originally used by companies, banks and later by the German military during WWII to encrypt messages. The main difference to classical cryptographic methods, was the fact that the cipher was polyalphabetic. The key changed for each individual letter you enciphered. So for example, you might press a `J` and end up with an `E` the first time and a `B` the second time.

The early Enigma machine consisted of a keyboard, a lampboard and three rotors with 26 letters each. When a key was pressed a letter flashed on the lampboard and the right rotor turned one step. Once the right rotor had made one full revolution, it kicked the middle rotor by one step and so forth, just like an [odometer](https://upload.wikimedia.org/wikipedia/commons/thumb/0/0b/Odometer_70000.jpg/800px-Odometer_70000.jpg). So if you set the rotors to A-B-C, the following would happen:

~~~
A-B-C -> A-B-D ... A-B-Z -> A-C-A
~~~

![Parts of the Enigma machine](../img/enigma_a.jpg)

When the German military saw the potential of the machine, they used various methods to insure better security. First they increased the number of rotors to four `4 * 3 * 2 = 24 permutations`. They then added a plugboard, which paired letters together with 10 wires `26! / (6! * 10! * 2^10) = 150'738'274'937'250 permutations`.

~~~
Total combinations: 1054560 * 150,738,274,937,250 = 158,962,555,217,826,360,000 ≈ 1.59 * 10^20
~~~

![Enigma plugboard](../img/plugboard.jpg)

So now that we know the different parts of an Enigma machine, lets have a look at how to set up the machine to encrypt and decrypt a message:

**The rotor order:** Numbered from one to three in Roman numerals (I-III), each rotor was wired up differently and when placed on the rack in different order, they gave a different output.

![Eingma rotor](../img/enigma_rotor.jpg)

**The ring setting:** The numbers displayed through little holes next to the rotors, indicated the ring setting. Each rotor was assigned a ring setting.

**The ground setting:** The key.

![Enigma ground setting](../img/enigma_b.jpg)

**Plugging:** Two letters could be connected together with a wire.

**The reflector wheel:** The circuit passed through the rotors and was then reflected back through the three rotors.

---

#### 🎓 Example:

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

---

The following steps were taken to ensure that both ends could communicate:

1. Both sender and recipient had to have the same machine, or at least both machines had to be configured so as to be in the same state. This means the same reflector wheel, rotor order, ring setting and ground setting were used to encrypt and decrypt the message.

2. Everyday these settings changed and so German operators were handed out keylists of all the different settings for the month. If the enemy got hold of a list, which they did sometimes, the list became useless once the month was over. Obviously, if there was any suspicion of a missing keylist, the Germans would have generated a new one. Keylists were either distributed in printed form or over radio as Morse code. The German Navy used ink that disappeared in water, so that when a ship sank the keylist was destroyed.

![Enigma keylist](../img/enigma_keylist.jpg)

Now if both ends have followed all these steps accordingly, the sender could encrypt `HELLO` with his machine, which might output something like `UZCFS`. The receiver can then type `UZCFS` into his machine and it should output `HELLO`.