
    asdf plugin-add kubectl https://github.com/asdf-community/asdf-kubectl.git
    asdf install kubectl 1.21.9

And a .tools-versions with:

    kubectl 1.21.9

Upgrade go:

    asdf list golang
    asdf install golang latest
    asdf global golang latest
