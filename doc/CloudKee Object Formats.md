CloudKee Stored Object Formats
==============================

The CloudKee format uses a few types of cryptographic objects. Namely, the use
of wrapped shared key shards and the password protected Root Device Key are the
two types of stored cryptographic objects that this document is interested to
address.

--------------------------------------------------------------------------------

### BlackRDK

The BlackRDK is essentially the basis for the security of all other key shards
and the compromise of this object would be catastrophic. A stretched password is
typically used to protect the RDK key in which it becomes a BlackRDK when under
the protection of a Password-derived key which encrypts the RDK. When the RDK is
unprotected (i.e. unwrapped for cryptographic operations), it becomes the RedRDK
. This uses the well known concept of Red/Black keys.

Below is a table of the BlackRDK format:

| ObjectName | Length (byte) | Description                                    |
-------------------------------------------------------------------------------
| Algo       | 1             | Indicates the algorithm used in the wrapping.  |
| IV         | 16            | Cryptographic IV.                              |
| RDK KeyMat | 32            | Contains the keymat for the RDK key.           |
| MAC        | 32            | MAC code for Algo + IV + RDK KeyMat            |

Below is a table of algorithm available for wrappingf the RDK KeyMat and also
deriving the MAC.

| AlgoName                   | ByteIndicator | Description                                                                            |
---------------------------------------------------------------------------------------------------------------------------------------
| Argon2-AES_CBC-HMAC_SHA256 | 0x01          | Uses Argon2 to stretch the password and AES_CBC for encryption and HMAC_SHA256 for MAC |


