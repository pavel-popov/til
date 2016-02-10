# Removing all non alpha-numeric chars from string in Go

    package main
    
    import (
    	"fmt"
    	"regexp"
    )
    
    func main() {
    	fmt.Println("Removing all non-alphanumeric characters from string")
    	src := "String with -123, non-alpha numeric chars removed: фыва234ё\"!№(;.,%Э"
    	re := regexp.MustCompile("[^a-zA-Z0-9а-яА-ЯёЁ]*")
    	fmt.Println(re.ReplaceAllString(src, ""))
    }


[play](http://play.golang.org/p/4cvGwt48i6)
