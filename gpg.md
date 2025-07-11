Decryption

    GPG_TTY=$(tty)
    gpg -d ./iam-alongstaffe.txt.gpg > iam-alongstaffe.txt

Expiry

To check keys

    gpg2 --list-keys
 
This describes how to renew GPG keys inc sub keys - how to renew

Essentially 

    gpg2 --edit-key <key_id>
    gpg> expire
    ....
    gpg> save

Don’t forget to save!
