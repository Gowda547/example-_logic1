# example-_logic1

////design
module logic2(
  input a,b,c,d,
  output f);
  
  assign f= (~a&b&c)|(~b&a)|(~a&b&~d);
endmodule


//testbench

module tb_logic2();
  reg a,b,c,d;
  wire f;
  
  
  logic2 uut(
    .a(a),
    .b(b),
    .c(c),
    .d(d),
    .f(f));
  
  initial begin
    $display("a=%b","b=%b","c=%b", "d=%b", a,b,c,d);
    $dumpfile("logic2.vcd");
    $dumpvars(0, tb_logic2);
    a=0; b=0; c=0; d=0;
    #10; a=0; b=0; c=0; d=1; 
    #10; a=0; b=0; c=1; d=0;
    #10; a=0; b=0; c=1; c=1;
    #10; a=0; b=1; c=0; d=0;
    
  end
endmodule
