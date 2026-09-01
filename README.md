# EX-NO-12-ELGAMAL-ALGORITHM
### NAME: KIRUTIKA K R
### REG NO: 212224230128

## AIM:
To Implement ELGAMAL ALGORITHM

## ALGORITHM:

1. ElGamal Algorithm is a public-key cryptosystem based on the Diffie-Hellman key exchange and relies on the difficulty of solving the discrete logarithm problem.

2. Initialization:
   - Select a large prime \( p \) and a primitive root \( g \) modulo \( p \) (these are public values).
   - The receiver chooses a private key \( x \) (a random integer), and computes the corresponding public key \( y = g^x \mod p \).

3. Key Generation:
   - The public key is \( (p, g, y) \), and the private key is \( x \).

4. Encryption:
   - The sender picks a random integer \( k \), computes \( c_1 = g^k \mod p \), and \( c_2 = m \times y^k \mod p \), where \( m \) is the message.
   - The ciphertext is the pair \( (c_1, c_2) \).

5. Decryption:
   - The receiver computes \( s = c_1^x \mod p \), and then calculates the plaintext message \( m = c_2 \times s^{-1} \mod p \), where \( s^{-1} \) is the modular inverse of \( s \).

6. Security: The security of the ElGamal algorithm relies on the difficulty of solving the discrete logarithm problem in a large prime field, making it secure for encryption.

## Program:
```
#include <stdio.h> 
long long powerMod(long long base, long long exp, long long mod) 
{ 
    long long result = 1; 
 
    while (exp > 0) 
    { 
        result = (result * base) % mod; 
        exp--; 
    } 
    return result; 
} 
long long modInverse(long long a, long long p) 
{ 
    long long i; 
 
    for (i = 1; i < p; i++) 
    { 
        if ((a * i) % p == 1) 
            return i; 
    } 
    return -1; 
} 
int main() 
{ 
    long long p, g, x, y; 
    long long m, k, c1, c2; 
    long long s, inverse, decrypted; 
    printf("Enter a prime number (p): "); 
    scanf("%lld", &p); 
    printf("Enter primitive root (g): "); 
    scanf("%lld", &g); 
 
    printf("Enter private key (x): "); 
    scanf("%lld", &x); 
    y = powerMod(g, x, p); 
    printf("\nPublic Key  = (%lld, %lld, %lld)", p, g, y); 
    printf("\nPrivate Key = %lld\n", x); 
 
    printf("\nEnter message (m): "); 
    scanf("%lld", &m); 
 
    printf("Enter random key (k): "); 
    scanf("%lld", &k); 
    c1 = powerMod(g, k, p); 
    c2 = (m * powerMod(y, k, p)) % p; 
 
    printf("\n--- Encryption ---\n"); 
    printf("Ciphertext c1 = %lld\n", c1); 
    printf("Ciphertext c2 = %lld\n", c2); 
    s = powerMod(c1, x, p); 
    inverse = modInverse(s, p); 
 
    decrypted = (c2 * inverse) % p; 
 
    printf("\n--- Decryption ---\n"); 
printf("Shared value = %lld\n", s); 
printf("Modular inverse = %lld\n", inverse); 
printf("Decrypted message = %lld\n", decrypted); 
return 0; 
}
```

## Output:
<img width="507" height="485" alt="image" src="https://github.com/user-attachments/assets/196f8984-7511-40ec-af50-9c2005e7b82d" />


## Result:
The program is executed successfully.
