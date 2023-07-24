 **customcircuit**
 
 This project is used to generate zero-knowledge circuits, proofs, and solidity verifiers.

 
 **Description**
 
 In this project, I have used Circom,  a zkSNARK framework for compiling zero-knowledge circuits. 
 It comes with its own domain-specific language (DSL) for writing circuits and tools to compile those circuits into artifacts.
 After the successful completion of the circuit, we will deploy it on the test network.

 
 **Getting Started**
 
 **Installing**
 
 Demo template is provided at https://github.com/gmchad/zardkat.
 For custom circuit need to made changes on circuit.circom.
 pragma circom 2.0.0;

/*This circuit template checks that c is the multiplication of a and b.*/  

template Multiplier2 () {  
   signal input a;
   signal input b;
   signal x;
   signal y;
   signal output q;

   component andGate =AND();
   component orGate =OR();
   component notGate =NOT();

   andGate.a<==a;
   andGate.b<==b;
   x<==andGate.out;
   notGate.in<==b;
   y<==notGate.out;
  orGate.a<==x;
  orGate.b<==y;
   q<==orGate.out;
 
}
template AND() {
    signal input a;
    signal input b;
    signal output out;

    out <== a*b;
}
template OR() {
    signal input a;
    signal input b;
    signal output out;

    out <== a + b - a*b;
}
template NOT() {
    signal input in;
    signal output out;

    out <== 1 + in - 2*in;
}

component main = Multiplier2();

code compiled using the command npx hardhat circom.
Try to use Gitpod.


**Author**

Baby Monal
