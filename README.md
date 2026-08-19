# EX-NO-9-RSA-Algorithm

## AIM:
To Implement RSA Encryption Algorithm in Cryptography

## Algorithm:


Step 1: Design of RSA Algorithm  
The RSA algorithm is based on the mathematical difficulty of factoring the product of two large prime numbers. It involves generating a public and private key pair, where the public key is used for encryption, and the private key is used for decryption.

Step 2: Implementation in Python or C 
This algorithm can be implemented in languages like Python or C by performing large integer calculations for key generation, encryption, and decryption, utilizing libraries for modular arithmetic if necessary.

Step 3: Algorithm Description  
1. Key Generation:
   - Select two large prime numbers \( p \) and \( q \).
   - Calculate \( n = p \times q \), which will be used as the modulus.
   - Compute the totient \( \phi(n) = (p - 1)(q - 1) \).
   - Choose a public exponent \( e \) such that \( e \) is coprime with \( \phi(n) \).
   - Compute the private key \( d \), which is the modular inverse of \( e \) mod \( \phi(n) \).

2. Encryption:
   - Convert the plaintext message \( M \) into a numerical form \( m \) (such that \( 0 \le m < n \)).
   - Compute the ciphertext \( c \) using the formula: \( c = m^e \mod n \).

3. Decryption:
   - Use the private key \( d \) to recover \( m \) from \( c \) using: \( m = c^d \mod n \).
   - Convert \( m \) back into the original message \( M \).

Step 4: Mathematical Representation  
- Encryption: \( E(m) = m^e \mod n \)
- Decryption: \( D(c) = c^d \mod n \)

Step 5: **Security Foundation  
The security of RSA relies on the difficulty of factoring large numbers; thus, choosing sufficiently large prime numbers for \( p \) and \( q \) is crucial for security.

## Program:
```
#include <stdio.h>
#include <math.h>

int gcd(int a, int b)
{
    while (b != 0)
    {
        int temp = b;
        b = a % b;
        a = temp;
    }
    return a;
}

int main()
{
    int p = 3, q = 11;
    int n, phi, e, d = 0;
    int msg, cipher, decrypted;

    // Calculate n
    n = p * q;

    // Calculate Euler's Totient
    phi = (p - 1) * (q - 1);

    // Choose public key e
    e = 3;

    // Find private key d
    for (d = 1; d < phi; d++)
    {
        if ((d * e) % phi == 1)
            break;
    }

    // Input message
    msg = 7;

    // Encryption: c = m^e mod n
    cipher = 1;
    for (int i = 0; i < e; i++)
        cipher = (cipher * msg) % n;

    // Decryption: m = c^d mod n
    decrypted = 1;
    for (int i = 0; i < d; i++)
        decrypted = (decrypted * cipher) % n;

    printf("p = %d\n", p);
    printf("q = %d\n", q);
    printf("n = %d\n", n);
    printf("phi(n) = %d\n", phi);

    printf("Public Key = (%d, %d)\n", e, n);
    printf("Private Key = (%d, %d)\n", d, n);

    printf("Original Message = %d\n", msg);
    printf("Encrypted Message = %d\n", cipher);
    printf("Decrypted Message = %d\n", decrypted);

    return 0;
}
```


## Output:
<img width="1726" height="655" alt="image" src="https://github.com/user-attachments/assets/d8076db7-e4f9-46ce-8de3-81d7c0585e95" />



## Result:
 The program is executed successfully.
