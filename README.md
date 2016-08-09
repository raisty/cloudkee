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
