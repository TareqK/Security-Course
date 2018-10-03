# Integrity

Integrity is the ability to detect unauthorized wiriting of data. Encryption provides *confidentiality*, but does not provide *integrity*.

## MAC 

MAC stands for **M**essage **A**uthentication **C**ide, which is used for integrity. It is used as a sort of checksum for the data. it is computed as a **CBC** residue, ie, it is the final block.