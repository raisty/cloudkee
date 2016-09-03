CloudKee Protocol
=================

CloudKee attempts to make storage of sensitive secrets much more robust and 
much harder to attack by using a variety of well known and well documented 
security techniques to mitigate differing types of attack vectors.

CloudKee uses a 2-Factor authentication approach to authenticate and unwrap a
root key known as a Root Device Key due to this key usually being kept on an
external device (thus the 2nd of the 2-Factor). The 1st Factor would be a 
password-derived key (i.e Argon2 or Scrypt) to stretch a user selected password
for the purpose of unwrapping and authenticating the wrapped Root Device Key 
which is also called an RDK key for short.

The RDK key when in it's protected mode is called a BlackRDK and when it is in
an active mode and unprotected is called a RedRDK. This uses the concept of
Red and Black keys to differentiate the different states of a cryptographic key.

Sensitive secrets (cryptographic keys and secrets) are "sharded" via Shamir 
Secret Sharing scheme into multiple pieces (KeyShards) for the purpose of making
it difficult to compromise a sensitive secret until enough shards are gathered
and the RDK is put into the RedRDK state to unwrap the wrapped KeyShards and the
unwrapped KeyShards and pieced back via Shamir Secret Sharing algorithm to form
back the original sensitive secret.

