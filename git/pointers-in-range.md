# Pointers inside range statement

It turned out that the address of the object inside range loop is changing between iterations:

    package main
    
    import "fmt"
    
    type Struct struct {
    	ID   int
    	Name string
    }
    
    var ss = []Struct{
    	Struct{1, "first"},
    	Struct{2, "second"},
    	Struct{3, "fourth"},
    	Struct{4, "fifth"},
    }
    
    func main() {
    	fmt.Println("Address of the object container variable is not changing inside range loop")
    	ch := make(chan bool)
    	go func() {
    		for _, s := range ss {
    			fmt.Printf("struct = %v, address = %p\n", s, &s)
    		}
    		ch <- true
    	}()
    	<-ch
    }

Result:

    Address of the object container variable is not changing inside range loop
    struct = {1 first}, address = 0x10434120
    struct = {2 second}, address = 0x10434120
    struct = {3 fourth}, address = 0x10434120
    struct = {4 fifth}, address = 0x10434120


http://play.golang.org/p/AmR1rD5oRx
