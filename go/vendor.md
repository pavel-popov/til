# Vendoring in GO

Starting from Go 1.5 you can use Vendoring for Go applications - simply put packages into `vendor` folder and they will be used as primary source for package lookup.


Example script for preparing vendor folder:


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
