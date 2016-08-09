# CloudKee
CloudKee is a Cloud-based Secure Key Storage system that allows you to safely store cryptgraphic secrets on any Cloud-based services 
without worrying on compromise of cryptographic secrets by strongly encrypting the shards of the cryptographic secrets by employing 
Shamir Secret Sharing to create key shares (shards) of the cryptographic secrets and then encrypting them with a unqiue key generated 
from a root key (Root Device Key) that a user keeps securely.

To further protect the Root Device Key from compromise (and therefore compromising all sharded cryptographic secrets), a Two Factor 
Authentication scheme that binds the Root Device Key to a secure hardware (i.e. Smart Card, TPMs, TEEs, HSMs ...) with a user password 
derived security key (SCRYPT derived) that secures the Root Device Key ensures that the secure hardware, the PIN code to the secure 
hardware and the Root Device Key's master password is necessary to decrypt sharded cryptographic secrets.

The scheme is hardened against Quantum Computing due to the encryption algorithm for the sharded cryptographic secrets using only 
symmetric encryption with strong key sizes and security algorithm (AES-256-CBC-PKCS7-HMAC-SHA-256).

Implementation Assumptions:
* Smart card as the PKI device for hardware binding of the Root Device Key.
* SCRYPT is preferred over Argon2 despite Argon2 being the winner of the PHC competition as Argon2 is rumoured to have it's algorithm upgraded to one with higher security and the fact that Argon2 is less popular than SCRYPT.
* AES-256-CBC-PKCS7-HMAC-SHA-256 for symmetric encryption and message authentication is used due to it being the most common AES algorithm available.
* Asymmetric key used for device binding would be RSA-2048 as this is the most commonly available PK algorithm found in Smart Cards, TPMs, TEEs, HSMs and other Secure Elements.
