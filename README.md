aes128
======
                         Advanced Encryption Stanadard-128 

2.1 Introduction
        
           Cryptography plays an important role in the security of data. Cryptography comes from Greek kryptós meaning "hidden", and gráphein, meaning "to write". It enables us to store sensitive information or transmit it across insecure networks so that unauthorized persons cannot read it. The urgency for secure exchange of digital data resulted in large quantities of different encryption algorithms. Parametric key algorithms are in general much faster to execute electronically than asymmetric key algorithms. Principal properties of cryptography are confidentiality, authenticity and integrity.
             Before the modern era, cryptography was concerned solely with message confidentiality (i.e., encryption) — conversion of messages from a comprehensible form into an incomprehensible one, and back again at the other end, rendering it unreadable by interceptors or eavesdroppers without secret knowledge (namely, the key needed for decryption of that message). In recent decades, the field has expanded beyond confidentiality concerns to include techniques for message integrity checking, sender/receiver identity authentication, digital signatures, interactive proofs, and secure computation, amongst others.
          In cryptography, the Advanced Encryption Standard (AES), also known as Rijndael, is a block cipher adopted as an encryption standard by the military. It has been analyzed extensively and is now used worldwide, as was the case with its predecessor, the Data Encryption Standard (DES). AES was after a 5-year standardization process. It became effective as a standard May 26, 2002. As of 2006, AES is one of the most popular algorithms used in symmetric key cryptography. It is available by choice in many different encryption packages. AES has a fixed block size of 128 bits and a key size of 128, 192, or 256 bits. [1]

             The cipher was developed by two Belgian cryptographers, Joan Daemen and Vincent Rijmen, and submitted to the AES selection process. Unlike DES (the predecessor of AES), it is  not a Feistel network. AES is fast in both software and hardware, is relatively easy to implement, and requires little memory. As a new encryption standard, it is currently being deployed on a large scale. 
                    
          In cryptography, encryption is the process of transforming information using an algorithm to make it unreadable to anyone except those possessing special knowledge, usually referred to as a key. The result of the process is encrypted information (in cryptography, referred to as ciphertext). In many contexts, the word encryption also implicitly refers to the reverse process, decryption (e.g. “software for encryption” can typically also perform decryption), to make the encrypted information readable again (i.e. to make it unencrypted).
                                    
2.2  AES Algorithm
2.2.1.The high level cipher Algorithm can be given as:
KeyExpansion using Rijndael's key schedule 
Initial Round 
1. SubBytes—a non-linear substitution step where each byte is replaced with another according to a lookup table. 
2. ShiftRows—a transposition step where each row of the state is shifted cyclically a certain number of steps. 
3. MixColumns—a mixing operation which operates on the columns of the state, combining the four bytes in each column 
4. AddRoundKey—each byte of the state is combined with the round key; each round key is derived from the cipher key using a key schedule. 
Final Round (no MixColumns) 
1. SubBytes 
2. ShiftRows 
3. AddRoundKey [10]
         The input and output for the AES algorithm each consist of sequences of 128 bits (digits with values of 0 or 1). These sequences will sometimes be referred to as blocks and the number of bits they contain will be referred to as their length. The Cipher Key for the AES algorithm is a sequence of 128, 192 or 256 bits. Other input, output and Cipher Key lengths are not permitted by this standard. With this form of cryptography, it is obvious that the key must be known to both the sender and the receiver; that, in fact, is the secret. The biggest difficulty with this approach, of course, is the distribution of the key.[2]
           The basic unit for processing in the AES algorithm is a, a sequence of eight bits treated as a single entity. The input, output and Cipher Key bit sequences described are processed as arrays of bytes that are formed by dividing these sequences into groups of eight contiguous bits to form arrays of bytes. For an input, output or Cipher Key denoted by a, the bytes in the resulting array will be referenced using one of the two forms, an or a[n], where n will be in one of the following ranges: 
Key length = 128 bits, 0 < n < 16; Block length = 128 bits, 0 < n < 16; 
Key length = 192 bits, 0 < n < 24; 
Key length = 256 bits, 0 < n < 32. 
All byte values in the AES algorithm will be presented as the concatenation of its individual bit values (0 or 1) between braces in the order {b7, b6, b5, b4, b3, b2, b1, b0}. These bytes are interpreted as finite field elements using a polynomial representation:
b7 x7 + b6 x6 + b5 x5  + b4 x4 + b3 x3 + b2 x2 + b1 x + b0  = bi xi      

          Internally, the AES algorithm’s operations are performed on a two-dimensional array of bytes called the State. The State consists of four rows of bytes, each containing Nb bytes, where Nb is the block length divided by 32. In the State array denoted by the symbol s, each individual byte has two indices, with its row number r in the range 0< r < 4 and its column number c in the range 0 < c < Nb. This allows an individual byte of the State to be referred to as either s(r,c) or s[r,c]. For this standard, Nb=4, i.e., 0 < c < 4.
    
                         
                         Fig 2.1: The Various Key Block Round Combinations in AES
             
2.3 Mathematical Support

2.3.1 Addition

        The addition of two elements in a finite field is achieved by “adding” the coefficients for the corresponding powers in the polynomials for the two elements. The addition is performed with the XOR operation (denoted by -      )i.e., modulo 2 - so that    1  1 = 0, 1   0 = 1, and 0  0 = 0 .Consequently, subtraction of polynomials is identical to addition of polynomials. Alternatively, addition of finite field elements can be described  as  the modulo 2 addition of corresponding bits in the byte. [2]
           
2.3.2 Multiplication

         In the polynomial representation, multiplication in GF (28 )  (denoted by ) corresponds with the multiplication of polynomials modulo an irreducible polynomial of degree 8. A polynomial is irreducible if its only divisors are one and itself. For the AES algorithm, this irreducible polynomial is   m(x) = x8 + x4 + x3 + x +1.  GF stands for Galois Field. [3]



2.3.3 Algorithm Specifications

            For the AES algorithm, the length of the input block, the output block and the State is 128 bits. This is represented by Nb = 4, which reflects the number of 32-bit words (number of columns) in the State.
         For the AES algorithm, the length of the Cipher Key, K, is 128, 192, or 256 bits. The key length is represented by Nk = 4, 6, or 8, which reflects the number of 32-bit words (number of columns) in the Cipher Key. For the AES algorithm, the number of rounds to be performed during the execution of the algorithm is dependent on the key size. The number of rounds is represented by Nr, where Nr = 10 when Nk = 4, Nr = 12 when Nk = 6, and Nr = 14 when Nk = 8. With this form of cryptography, it is obvious that the key must be known to both the sender and the receiver; that, in fact, is the secret. The biggest difficulty with this approach, of course, is the distribution of the key.
         For both its Cipher and Inverse Cipher, the AES algorithm uses a round function that is composed of four different byte-oriented transformations: 1) byte substitution using a substitution table (S-box), 2) shifting rows of the State array by different offsets, 3) mixing the data within each column of the State array, and 4) adding a Round Key to the State. [2]
            
2.4  Cipher
        
          At the start of the Cipher, the input is copied to the State array using the conventions described in. After an initial Round Key addition, the State array is transformed by implementing a round function 10, 12, or 14 times (depending on the key length), with the final round differing slightly from the first Nr -1 rounds. The final State is then copied to the output as described in. The round function is parameterized using a key schedule that consists of a one-dimensional array of four-byte words derived using the Key Expansion routine. The operation of a cipher usually depends on a piece of auxiliary information, called a key or, in traditional NSA parlance. [2]
      The encrypting procedure is varied depending on the key, which changes the detailed operation of the algorithm. A key must be selected before using a cipher to encrypt a message. Without knowledge of the key, it should be difficult, if not nearly impossible, to decrypt the resulting cipher into readable plaintext. In classical cryptography, ciphers were distinguished from codes. Codes operated by substituting according to a large codebook which linked a random string of characters or numbers to a word or phrase.
       When using a cipher the original information is known as plaintext, and the encrypted form as ciphertext. The ciphertext message contains all the information of the plaintext message, but is not in a format readable by a human or computer without the proper mechanism to decrypt it; it should resemble random gibberish to those not intended to read it.

                                         
                              Fig 2.2: Encryption of Block Cipher AES 128

2.4.1 Sub-Bytes Transformation
      
         The Sub-Bytes transformation is a non-linear byte substitution that operates independently on each byte of the State using a substitution table (S-box).
        This S-box, which is invertible, is constructed by composing two transformations:
1. Take the multiplicative inverse in the finite field GF (28), the element {00} is mapped to itself.
2. Apply the following affine transformation (over GF (22)).
             b'i = bib(i+4)mod 8b(i+5)mod 8b(i+6)mod 8b(i+7)mod 8ci
      In the SubBytes step, each byte in the array is updated using a substitution box, the Rijndael S-box. This provides the non-linearity in the cipher. The S-box used is derived from the multiplicative inverse, known to have good non-linearity properties. The S-box is constructed by combining the inverse function with an invertible affine transformation. [2]

                       
                                 Fig 2.3: Sub Bytes Transformation Step
                   

           Fig: S-box 2.4: substitution values for the byte xy (in hexadecimal format).


2.4.2 Shift Rows Transformation

         In the Shift Rows transformation, the bytes in the last three rows of the State are cyclically shifted over different numbers of bytes. The first row, r = 0, is not shifted. This has the effect of moving bytes to positions in the row (i.e., lower values of c in a given row), while the “lowest” bytes wrap around into the “top” of the row (i.e., higher values of c in a given row). Similarly, the third and fourth rows are shifted by offsets of two and three respectively. The shift row transformation is more substantial than it may first appear. This is because the State, as well as the cipher input and output, are dependent on it. However, shift-invariance is desirable in stereo matching intensity profiles from the corresponding row. This is where the matrix representation of the state array becomes important. [3]
                    
                        Fig 2.5: Shift Rows Transformation.

2.4.3 Mix Column Transformation

           In the MixColumns step, the four bytes of each column of the state are combined using an inverse transformation. The MixColumns function takes four bytes as input and outputs four bytes, where each input byte affects all four output bytes. Together with ShiftRows, it provides the cipher. [2]
                                      
                                              Fig 2.6: Mix Columns Transformation

2.4.4 Add Round Key step
         AES-128 is a 10 round block cipher. In the AddRoundKey transformation, a Round Key is added to the State by a simple bitwise XOR operation. Each Round Key consists of Nb words from the key schedule Those Nb words are each added into the columns of the State, such that 

where [wi] are the key schedule words described and round is a value in the range 0 < round < Nr. In the Cipher, the initial Round Key addition occurs when round = 0, prior to the first application of the round function. The application of the AddRoundKey transformation to the Nr rounds of the Cipher occurs when 1 < round < Nr. 
             In the AddRoundKey step, the subkey is combined with the state. For each round, a subkey is derived from the main key using Rijndael's key schedule; each subkey is the same size as the state. The subkey is added by combining each byte of the state with the corresponding byte of the subkey using bitwise XOR. [4]
                        

                                          Fig 2.7: Add Round Key Transformation step

2.5  Key Expansion
         The AES algorithm takes the Cipher Key, K, and performs a Key Expansion routine to generate a key schedule. To look at key expansion, it is most convenient to think of an AES key as a list of 16 strings, each of which is an 8 bit byte. The Key Expansion generates a total of Nb (Nr + 1) words: the algorithm requires an initial set of words, and each of the Nr rounds requires Nb words of key data. The resulting key schedule consists of a linear array of 4-byte words, denoted [wi], with i in the range 0 < i < Nb(Nr + 1).  It is important to note that the Key Expansion routine for 256-bit Cipher Keys is slightly different than for 128- and 192-bit Cipher Keys. [5]
        The Xor-ing of the sub-key before the first round and the last round affects every bit of the round result. Function used in the Key Expansion routine that takes a four-byte word. The key expansion consists of the number of round key bits equaling 32 bits x Block Length x (Round Numbers + 1). So the memory storage depends on the size of the main key length. For key expansion, the decryption process is the same. The keys are produced on-line and on the fly because every subsequent word is equal to the Xor of the previous word. The Key Expansion step merely supplies a much expanded (and transformed) In the case of the AES, there are a number of rounds, each needing its own key, so the actual key is ``stretched out'' and transformed to give portions of key for each round. Totally, the number of registers needed for the implementation of the Key Expansion transformation within the coprocessor is 2 (or at maximum 3 for keys longer than 16 bytes). [2]
                         
                         Fig2.8: Structure of AES Algorithm
2.6  Inverse Cipher
        The Cipher transformations in can be inverted and then implemented in reverse order to produce a straightforward Inverse Cipher for the AES algorithm. Inverse cipher is nothing but the decrypted output using the same key as that used to get the cipher text. That is inverse ciphering is known as deciphering or decryption. [1]     
                            
                                            Fig 2.9: Decryption for AES 128
2.6.1 Inverse Shift Row Transformation
      Inverse Shift Rows is the inverse of the Shift Rows transformation. The bytes in the last three rows of the State are cyclically shifted over different numbers of bytes (offsets). The first row, r = 0, is not shifted. The bottom three rows are cyclically shifted by Nb - shift(r,Nb) bytes, where the shift value shift(r,Nb) depends on the row number. 

                           Fig 2.10: Inverse shift rows Transformation.
2.6.2 Inverse Sub Bytes Transformation
        Inverse Sub Bytes is the inverse of the byte substitution transformation, in which the inverse S-box is applied to each byte of the State. This is obtained by applying the inverse of the affine transformation followed by taking the multiplicative inverse in GF (28).                         
          Fig: Inverse S-box 2.11: substitution values for the byte xy (in hexadecimal format).
2.6.3 Inverse Mix Columns Transformation
         Inverse Mix Columns is the inverse of the Mix Columns transformation. Inverse Mix Columns operates on the State column-by-column, treating each column as a four-term polynomial as described. The columns are considered as polynomials over GF (28) and multiplied modulo x4 + 1 with a fixed polynomial a-1(x).

2.6.4 Inverse Add round key Transformation
    AddRoundKey transformation, which was described earlier, is the same.

2.7 Block cipher modes of operation
          In cryptography, a block cipher operates on blocks of fixed length, often 64 or 128 bits. Because messages may be of any length, and because encrypting the same plaintext under the same key always produces the same output (as described in the ECB section below), several modes of operation have been invented which allow block ciphers to provide confidentiality for messages of arbitrary length. A block cipher breaks the plaintext into blocks of the same size, each of which is then encrypted (that is like a substitution on very big characters - 64-bits or more). Block ciphers are the most basic, as they use a single key to transform a block of text. Block cipher is a symmetric or secret or single or one or shared or private key cipher. The most important symmetric (meaning the same key is used for both encryption and decryption) algorithms are block ciphers. [10]     
          The earliest modes described in the literature (eg, ECB, CBC, OFB and CFB) provide only confidentiality or message integrity, but do not perform both simultaneously. ECB stands for Electronic code book and CBC stands for Cipher Block Chaining. A block cipher is a method of encrypting text (to produce ciphertext) in which a cryptographic key and algorithm are applied to a block of data (for example, 64 contiguous bits) at once as a group rather than to one bit at a time. Ensures that all subsequent blocks result in ciphertext that doesn't match that of the first encrypting

Electronic Code Book (ECB):
          In cryptography, the simplest mode of operation used with a block cipher to provide the complete encryption algorithm. Each block of regular text (plaintext) is encrypted with the cipher as a unit and turned into encrypted text (ciphertext). The weakness in the electronic code book (ECB) method is that repeating plaintext generates repeating ciphertext from which cryptanalysis can more easily derive the secret keys.
            Electronic Code Book (ECB) is a mode of operation for a block cipher, with the characteristic that each possible block of plaintext has a defined corresponding ciphertext value and vice versa. In other words, the same plaintext value will always result in the same ciphertext value. Electronic Code Book is used when a volume of plaintext is separated into several blocks of data, each of which is then encrypted independently of other blocks. In fact, Electronic Code Book has the ability to support a separate encryption key for each block type. In some senses, it doesn't provide serious message confidentiality, and it is not recommended for use in cryptographic protocols at all.
        However, Electronic Code Book is not a good system to use with small block sizes (for example, smaller than 40 bits) and identical encryption modes. This is because some words and phrases may be reused often enough so that the same repetitive part-blocks of ciphertext can emerge, laying the groundwork for a codebook attack where the plaintext patterns are fairly obvious. However, security may be improved if random pad bits are added to each block. On the other hand, 64-bit or larger blocks should contain enough unique characteristics (entropy) to make a codebook attack unlikely to succeed. 
           In terms of error correction, any bit errors in a ciphertext block affect decryption of that block only. Cipher dependency is not an issue in that reordering of the ciphertext blocks will only reorder the corresponding plaintext blocks, but not affect decryption. ECB mode can also make protocols without integrity protection even more susceptible to replay attacks, since each block gets decrypted in exactly the same way. [10]
                
                     
              Fig 2.12: ECB mode encryption and decryption block diagrams
    In Short about Electronic Code Book:
It is a mode of operation for block cipher
It is a simple block mode
Plain text is separated into many blocks
More prone to attacks
Can be used to locate known data

2.7.2 Cipher Block Chaining (CBC):
         Cipher block chaining uses what is known as an initialization vector (IV) of a certain length. One of its key characteristics is that it uses a mechanism that causes the decryption of a block of ciphertext to depend on all the preceding ciphertext blocks. A single bit error in a ciphertext block affects the decryption of all subsequent blocks. Rearrangement of the order of the ciphertext blocks causes decryption to become corrupted. Basically, in cipher block chaining, each plaintext block is XORed with the immediately previous ciphertext block, and then encrypted..
         Identical ciphertext blocks can only result if the same plaintext block is encrypted using both the same key and the initialization vector, and if the ciphertext block order is not changed. It has the advantage over the Electronic Code Book mode in that the XOR'ing process hides plaintext patterns. 
          The initialization vector should be different for any two messages encrypted with the same key. Though the initialization vector need not be secret, some applications may find this desirable. Also, to make each message unique, an initialization vector must be used in the first block. There is no need for the IV to be secret, in most cases. For CBC and CFB, reusing an IV leaks some information about the first block of plaintext, and about any common prefix shared by the two messages. For OFB and CTR, reusing an IV completely destroys security. In CBC mode, the IV must, in addition, be randomly generated at encryption time. 
        Many more modes of operation for block ciphers have been suggested. Some of them have been accepted, fully described (even standardised), and are in use. Tweakable narrow-block encryption (LRW) mode, and wide-block encryption (CMC and EME) modes, designed to securely encrypt sectors of a disk, are described in the article devoted to disk encryption theory. [10]

                            
                                
        CBC has been the most commonly used mode of operation. Its main drawbacks are that encryption is sequential and that the message must be padded to a multiple of the cipher block size. One way to handle this last issue is through the method known as ciphertext.        Note that a one-bit change in a plaintext affects all following ciphertext blocks, and a plaintext can be recovered from just two adjacent blocks of ciphertext. As a consequence, decryption can be parallelized, and a one-bit change to the ciphertext causes complete corruption of the corresponding block of plaintext, and inverts the corresponding bit in the following block of plaintext. [12]

2.7.3 Optimization of Cipher
       On systems with 32-bit or larger words, it is possible to speed up execution of this cipher by combining SubBytes and ShiftRows with MixColumns, and transforming them into a sequence of table lookups. This requires four 256-entry 32-bit tables, which utilizes a total of four kilobytes (4096 bytes) of memory—one kilobyte for each table. A round can now be done with 16 table lookups and 12 32-bit exclusive-or operations, followed by four 32-bit exclusive-or operations in the AddRoundKey step. Combinational optimization techniques are unsuitable for attacks on the knapsack cipher. This remark is contrary to the claims of Spellman. [2]
       If the resulting four kilobyte table size is too large for a given target platform, the table lookup operation can be performed with a single 256-entry 32-bit table by the use of circular rotates.Using a byte-oriented approach it is possible to combine the SubBytes, ShiftRows, and MixColumns steps into a single round operation. The design target was optimization of area and cost of the circuit used and security.

2.7.4 Security
       As of 2006, the only successful attacks against AES implementations have been side channel attacks. The National Security Agency (NSA) reviewed all the AES finalists, including Rijndael, and stated that all of them were secure enough for US Government non-classified data. In June 2003, the US Government announced that AES may be used for classified information. [10]
          The design and strength of all key lengths of the AES algorithm (i.e., 128, 192 and 256) are sufficient to protect classified information up to thea level. The implementation of AES in products intended to protect national security systems and/or information must be reviewed and certified by NSA prior to their acquisition and use. AES-Security provides for the World's Toughest Environments Facility Security and Residential Security.There is a risk that some way to improve such attacks might be found and then the cipher could be broken. AES has a very neat algebraic description. This has not yet led to any attacks, but some researchers feel that basing a cipher on a new hardness assumption is risky. Optimization of security is one of the major concerns for any of the ciphers being used. Several cryptography experts have found problems in the underlying mathematics of the proposed attack, suggesting that the authors may have made a mistake in their estimates. 
       There is no encryption standard or code that cannot be broken. But the time taken to break a code may vary from a few seconds to about trillions of years. Some cryptographers worry about the security of AES. They feel that the margin between the number of rounds specified in the cipher and the best known attacks is too small for comfort. Advanced Encryption Standard is an Independent Member of Hafilsa Security. There is a risk that some way to improve such attacks might be found and then the cipher could be broken. This once again shows how hard getting security right actually is.Whether this line of attack can be made to work against AES remains an open question. [12]
        There are several such known attacks on certain implementations of AES. Some say the attack is not practical over the internet with a distance of one or more hops; Bruce Schneier called this type of research a "nice timing attack." The author suggests that the algorithm is at fault for making it difficult for implementers to make fast-but-constant-time implementations, and then they list a few algorithms that don't have this limitation. Background information is provided, which is relevant to claims of key recovery attacks on the Advanced Encryption Standard (AES). Some of the cipher suites may not be enabled for security setup of startup time.
      AES introduces a higher level of security from past protocols by providing protection. This protects even more of the data packet from eavesdropping and tampering. This has not yet led to any attacks, but some researchers feel that basing a cipher on a new hardness assumption is risky. Advanced Encryption Standard has been supplying commercial and domestic customers with quality security for over 5 years. [11]


2.8 Applicaions of AES
       Rijndael is free for any use public or private, commercial or non-commercial. Care should be taken when implementing AES in software. Like most encryption algorithms, Rijndael was designed on big-endian systems. For this reason, little-endian systems return correct test vector results only through considerable byte-swapping, with efficiency reduced as a result. Careful choice must be made in selecting the mode of operation of the cipher.
The most prominent applications are:
Government and Military Organisation: Encryption is mostly required in the government and military to transfer secret information. Advanced Encryption Standard (AES) encryption standard has been developed widely to be used in the US government and military purposes. This security is protected, provided the key is secure between the using parties. Such type of encryption is quite necessary as it contains information related to high level security. Advanced Encryption Standard (AES) has been approved in 1998 is being followed as a standard as encryption in government, military and space applications since then. And it is being used more widely since 2006, in US government appications. [14]                                          
Computer Security: Advanced Encryption Standard (AES) since 2006, has not been used in government applications but also in day to day applications, such as in encrytping emails and other computer based information. The application specific Software for both AES encryption and decryption available allows user information to be encrypted securely, provided the key is securly maintained between the users. [12]
Networks ( Internet e-commerce ):  With the gain in prominence of online or internet transactions, security of transfer and storage of user data or information has become of utmost importance. For this purpose, a strong encryption standard such as AES is being used. [11]
Mobile Telephones: Mobiles, now a days can be used for more than just communication. Thus with the recent advancements, it has become necessary to use, usually AES encryption along with information transfer. [15]
Wireless: The Advanced Encryption Standard is used by the US Mobile Phones and PDAs and Multimedia Phones for downloads for wireless services.
Bluetooth: Some of the bluetooth devices use AES encryption as bluetooth devices can be easily attacked and information can be stolen or tampered by any other user if proper security is not provided during information transfer.
ATM (Automated Teller Machines): The user specific codes and sensitive information used in ATMs is coded using the strong AES encryption.
There are many more applications of AES encryption and decryption. Encryption is also used in digital rights management to prevent unauthorized use or reproduction of copy righted material.
2.9 Conclusion
         The project Implementation of AES-128 using VHDL code has been designed to be readily implemented on hardware. It has been designed in Active HDL 7.1 and its working has been verified on that software. This project also compares the less secure ECB model and the more secure CBC model. The various applications, security issues and optimization of the cipher have been discussed in this project. As the AES-128 standard is quite secure, it is widely used by the U.S Government, military and in ATMs for secure data transmission. 
 





