gpg --list-secret-keys --keyid-format LONG
gpg --armor --export <key-id>
# it will show PUBLIC KEY

git config --global user.signingkey 3AA5C34371567BD2
git config --global commit.gpgsign true
