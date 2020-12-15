---
  title: "An Intro to Cryptography"
  content: "What is Cryptography? How Does RSA Play Into It?"
---


### What is Cryptography?

Cryptography refers to the process of securing communication in the presence of third parties.

 Say Alice wants to send an important message to her friend, Bob. Under normal circumstances, sending this message wouldn't be a problem, but they recently realized that their other friend, Eve, wants to learn what they're talking about. They want to make sure that Eve can’t decipher it, so they must share the message using a secret language. Alice may hide her message which can only be accessed by a private key owned by Bob. This way, since Eve doesn’t have a private key, Eve won’t be able to understand the message.

This technology of sharing secret messages is used worldwide to ensure safe interactions on the internet. Today, Advanced Encryption Standard (AES) is used to decrypt messages. With brute force, it would take trillions of years to break the encryption.


### What is RSA and How Does it Work?

Using RSA encryption, messages are encrypted with a code, known as a public key, which can be shared openly. Once a message has been encrypted with the public key, it can only be decrypted by another key, known as the private key, which must be kept secret.

So, how does RSA actually work?

First, two entities each need to set up their own key pairs and share the public key with one another. The two must keep their private keys secret in order for their communications to remain secure.
Once the first sender has the public key of the recipient of their message, they can use it to encrypt the data that they want to keep secure. Once their data has been encrypted by the public key, it can only be decrypted by the private key from the same key pair.

When the recipient receives the encrypted message, they use their private key to access the data. If the recipient wants to return some type of communication in a secure way, they can then encrypt their message with the public key of the party they are communicating with. Again, once it has been encrypted with the public key, the only way that the information can be accessed is through the matching private key.

In this way, RSA encryption can be used by previously unknown parties to securely send data between themselves. Significant parts of the communication channels that we use in our online lives were built up from this foundation.
