# 4 bit magnitude comparator


## DESCRIPTION:

"dvsd_cmp" is a 4 bit magnitude comparator.


**Input  A [MSB:LSB]**: A_in  

**Input  B [MSB:LSB]** : B_in

**Output M [MSB:LSB]** : less_than equal_to greater_than


## MODULES:

1. dvsd_cmp

## Code

```v

module dvsd_cmp(
        //Input A        
A_in,                                                                                      
        //Input B
B_in,                                                      
        //When A is less than B, it is high
less_than,                                                                                                                                  
        //When A is equal to B, it is high
equal_to,
        //When A is greater than B, it is high
greater_than                                                                                                                                                                                                                                                      
);
        //Declaration of Input Ports.
    input [3:0] A_in;
    input [3:0] B_in;
        //Declarations of Output Ports.
    output less_than;
    output equal_to;
    output greater_than ;
        //Internal variables
        //reg declarations
     reg less_than;
     reg equal_to;
     reg greater_than;
        //When the inputs  A or B are changed then execute this block
    always @(A_in or B_in)
 begin
        //This block checks if A is Greater than B, Greater than is high
       if(A_in > B_in)                              
           begin                                        
                      less_than = 4'b0;      
                      equal_to =4'b0;
                      greater_than = 4'b1;    
           end
        //This block checks if A is equal to B, Equal to is high
       else if(A_in == B_in)                    
           begin                            
                      less_than = 4'b0;
                      equal_to = 4'b1;
                      greater_than = 4'b0;    
           end
        //Otherwise -This block checks for A less than B, Less than is high          
       else                                                  
           begin                                                  
                      less_than = 4'b1;
                      equal_to = 4'b0;
                      greater_than =4'b0;
        end
end
        //End of a module
endmodule
```



## Testbench for dvsd_8216m3

```

`timescale 1ns / 1ps

module tb_dvsd_cmp;

    // Inputs
    reg [3:0] A_in;
    reg [3:0] B_in;

    // Outputs
    //Declarations of internal wire
    wire less_than;    
    wire equal_to;
    wire greater_than;

    // Instantiate the Unit Under Test (UUT)
    dvsd_cmp uut (
        .A_in(A_in),
        .B_in(B_in),
        .less_than(less_than),
        .equal_to(equal_to),
        .greater_than(greater_than)
    );

    initial begin
    //dump file
    $dumpfile("tb_dvsd_cmp.vcd");                                        
    $dumpvars(0,tb_dvsd_cmp);
    //Applying input values
        A_in = 1000;    
        B_in = 1001;    
        #100;

        A_in = 0010;    
        B_in = 1110;    
        #100;

        A_in = 1010;    
        B_in = 1010;      
        #100;

        A_in = 0111;      
        B_in = 0110;      
        #100;

        A_in = 1011;        
        B_in = 1111;          
        #100;

        A_in = 0011;        
        B_in = 1101;        
        #100;

        A_in = 1111;        
        B_in = 1111;          
        #100;

        A_in = 0001;          
        B_in = 1100;          
        #100;

        A_in = 0101;            
        B_in = 0100;                      
        #100;

        A_in = 0110;            
        B_in = 1001;                      
        #100;

        A_in = 0000;            
        B_in = 0000;                      
        #100;

        A_in = 1100;            
        B_in = 0011;                      
        #100;
        
        A_in = 1000;    
        B_in = 1001;    
        #100;

        A_in = 0010;    
        B_in = 1110;    
        #100;

        A_in = 1010;    
        B_in = 1010;      
        #100;

        A_in = 0111;      
        B_in = 0110;      
        #100;

        A_in = 1011;        
        B_in = 1111;          
        #100;

        A_in = 0011;        
        B_in = 1101;        
        #100;

        A_in = 1111;        
        B_in = 1111;          
        #100;

        A_in = 0001;          
        B_in = 1100;          
        #100;

        A_in = 0101;            
        B_in = 0100;                      
        #100;

        A_in = 0110;            
        B_in = 1001;                      
        #100;

        A_in = 0000;            
        B_in = 0000;                      
        #100;

        A_in = 1100;            
        B_in = 0011;                      
        #100;
    end    
endmodule


```
