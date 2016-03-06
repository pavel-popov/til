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
        for _, s := range ss {
    		fmt.Printf("struct = %v, address = %p\n", s, &s)
    	}
    }

Result:

    Address of the object container variable is not changing inside range loop
    struct = {1 first}, address = 0x10434120
    struct = {2 second}, address = 0x10434120
    struct = {3 fourth}, address = 0x10434120
    struct = {4 fifth}, address = 0x10434120


http://play.golang.org/p/AmR1rD5oRx


So, it's better to have a slice of pointers that slice of structs:


    package main
    
    import "fmt"
    
    type Struct struct {
    	ID   int
    	Name string
    }
    
    var sp = []*Struct{
    	&Struct{1, "first"},
    	&Struct{2, "second"},
    	&Struct{3, "fourth"},
    	&Struct{4, "fifth"},
    }
    
    func main() {
    	fmt.Println("Address of the object container variable is not changing inside range loop")
    
    	for _, s := range sp {
    		fmt.Printf("struct = %v (%p), address = %p\n", s, s, &s)
    	}
    
    }

Result:

    Address of the object container variable is not changing inside range loop
    struct = &{1 first} (0x1e1f38), address = 0x1040a130
    struct = &{2 second} (0x1e1f48), address = 0x1040a130
    struct = &{3 fourth} (0x1e1f58), address = 0x1040a130
    struct = &{4 fifth} (0x1e1f68), address = 0x1040a130
