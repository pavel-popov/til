# Vendoring in GO

Starting from Go 1.5 you can use Vendoring for Go applications - simply put packages into `vendor` folder and they will be used as primary source for package lookup.


### Manual handling vendor folder

You can manually support the content of vendor folder:

    # assuming you're in the root folder of your project
    mkdir vendor
    cd vendor
    
    # download packages here
    GOPATH=`pwd` go get -d -v \
        github.com/RichardKnop/machinery/v1 \
        gopkg.in/inconshreveable/log15.v2 \
        golang.org/x/net/websocket \
        github.com/naoina/toml \
        github.com/mhale/smtpd \
        github.com/satori/go.uuid \
        github.com/jhillyerd/go.enmime \
        github.com/bluele/slack \
        github.com/labstack/echo \
        github.com/schmooser/go-echolog15
    
    # moving everything from src to vendor
    mv src/* . && rmdir src
    
    # removing .git folders
    find . | grep "\.git$" | xargs rm -rf


### Using package manager

There are a lot of package managers written for Go. There is a list in official Go' Github repo - https://github.com/golang/go/wiki/PackageManagementTools

I personally prefer [rancher/trash](https://github.com/rancher/trash) because it does what should be done. The only thing I noticed is that it often misses dependent packages of vendored packages, so you have to manually add them into your `trash.yml` file.

Luckily enough, this is a rare task.
