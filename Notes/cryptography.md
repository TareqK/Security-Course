# Cryptography 

Missed lecture 8/9/2018

## Important Things in Cryptography 

- Confidentiality --> of the information.
- Integrity --> tamper proofing.
- Availability --> of the service.

These are the 3 most important aspects of security.
Other important factors are :

- Authenticity/Authentication --> Whom am i talking to.
- Accountability --> Who did what and how and when(logs and such).
- Non-Repudiation --> You are legally responsible.

## Terminology

- Cryptology --> the art and science of making and breaking secret codes.
- Cryptography --> Making secret codes.
- Cryptoanalysis --> breaking secret codes.
- Crypto --> all of the above.

- A cipher or cryptosystem --> ecrypts plaintext
     - the result is ciphertext.
     - we decrypt ciphertext to get plaintext.
     - a key is used to configure a cryptosystem.
     - a symmetric key cryptosystem uses the same key to encrypt and decrypt.
     - a public key cryptosystem uses a public key to encrypt and a private key to decrypt --> asymmetric.

---

## Designing a Crypto System

### Basic Assumption

- The system is completely known to the attacker.
- Only the key is secret.
- The algorithms are not secret, because its practically easier to think that way, and it has been shown that secret algorithms are insecure once found out usually(due to poor implementation and relying on the secrecy of the algorithm) --> Kerkhoffs Principle. 
- Public algorithms = better auditing.

Crypto is a **black box**, but the technique is known, and the key is not.

---

### Good Systems
- A system is considered secure if the best way to break a system is to know all the keys. If any 
shortcut attack is known, then the system is insecure. But there are some cases where an insecure cipher might be harder to break than a secure cipher. 

---

## Ciphers 

### Historical Ciphers

- [Ceasar's Cipher](http://practicalcryptography.com/ciphers/caesar-cipher/) --> Shift the letter by 3 --> Also known as simple substitution.
- [Not so Simple Substitution](https://crypto.stackexchange.com/questions/35633/not-so-simple-substitution-cipher) --> Shift each letter by n where \(0<n<26\).

    Both Ceaser's Cipher and NSS are easy to break with **brute force** or **Exahstative Key Search**.

    A better form of NSS is to shift each letter individually by a different amount. In this case, we have 26! complexity, which is around 2<sup>88</sup> possible keys. DES has 2<sup>56</sup> keys, and was considered secure for quite some time(single DES is no longer considered secure).

    However, this is still a breakable text. We can use something called **Frequncy Key Search**, where we look for  letters that are repeated a lot or a little and, assuming we have a sufficient amount of text, we can find the key. This is because the ciphertext **inherits** the properties of the plaintext.  One way to get around this is to use something like the playfair cipher, or some form of matrix substitution.

- [playfair cipher](https://en.wikipedia.org/wiki/Playfair_cipher) -->  joins every 2 charecters to hide their frequency

- [Double Transposition](https://www.dcode.fr/double-transposition-cipher) --> Permute rows and columns based on some key.

- [One-Time Pad](https://en.wikipedia.org/wiki/One-time_pad)  --> XOR the Plaintext with the key the same length as the mesage. This method cannot be cracked if the key(called the one-time pad) is **truly random**(no advantage of 0 bits over 1 bits and vice versa), but is impractical because of the difficulty of key exchange. If an agent changes the key, then the text can be manipulated to produce any message desired as long as it is the length of the key. There is no way to know which key is correct.

    [Mathemtaical proof of OTP](https://crypto.stackexchange.com/questions/20748/proving-the-semantic-security-of-the-one-time-pad/20749#20749)

    &quot;Basically, The main point in any security proof for the one-time pad is that xoring a plaintext with a (uniformly) random bit string yields a (uniformly) random bit string no matter what the plaintext was.

    Therefore, picking some C uniformly at random is, in highly informal terms, essentially equivalent to being given that very same C as a ciphertext since a one-time pad ciphertext looks just like a uniformly random bit string to an attacker who doesn't have any information about the key.&quot;

    The one time pad is **provably** secure, because :
    
       1. The cipher text gives no info about the plantext.
       2. All plaintexts are equally likely.

    However, since the key and the message are the same size, we have to send twice the data in order to transfer the same amount of information. While mathematically secure, OTP is not a practical method of encryption. Besides, we need to secure sending the key, and since we can securely send the key, why not just securely send the message ?

- Ohter techniques : Zimmerman Telegram(WW1), Midway/Coral sea(WW2), Purple(WW2 Japan), Enigma(WW2 Germany).

    The [Egnima Machine](https://en.wikipedia.org/wiki/Enigma_machine) used by WW2 germany, caused a quality shift in encryption systems. It used a mechanical/electrical system that encoded messages.

- Post WW2 : After ww2, and the PC revolution, there was more need to protect data, leading to the creation of  Standards like DES(70s), AES(90s), the invention of public key cryptography(70s), and crypto confrences started happening(80s) and the crypto genie was out of the bottle.

    [Claude Shannon](https://en.wikipedia.org/wiki/Claude_Shannon), The founder of information theory, laid out some principles for secret systems  : 

    1. Confusion --> Obscure the relationship betwen plaintext and ciphertext. 
    
    2. Diffusion --> spread plaintext statistics through the ciphertext(no one-to-one mapping between changes to plaintext and the genreated ciphertext, This is also called the avalanche effect sometimes). 
    
    
---


Ciphers Generally use 2 things to hide the plaintext.

- Substitution --> Replace a letter with a letter.
- Shuffling --> move around letters in the message.


---








