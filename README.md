lang-dryad
==========

Dryad Language Library for the SugarJ Framework (http://sugarj.org)

## About

The Dryad Language Library uses code based on the Dryad Compiler (https://strategoxt.org/Stratego/TheDryadCompiler) to enable developing with a mixture of Java and Bytecode. As the compiler is written in Stratego/XT as well not only source- but also compiletime modifications can be realized using Stratego transformations.

## Why should I use it?

By being able to hook into the compilation process transformations can use the informations collected by the compiler like the expected and actual type.

[This example](https://github.com/thewilli/lang-dryad/blob/master/case-studies/dryad/src/test/compilermods/CompilerModTest1.sdr) uses type information to allow the usage of classes that implement a certain [Interface](https://github.com/thewilli/lang-dryad/blob/master/case-studies/dryad/src/test/compilermods/IntInterface.sdr) to be used instead of *int* values:

    		IntContainer cont1 = new IntContainer(2);
    		IntContainer cont2 = new IntContainer(7);
    		IntContainer cont3 = new IntContainer(3);
    		int a,b,c;
    		a = cont1;
    		b = 2 + cont2 * cont1 - cont3;
    		c = a * (b + cont2 + 5);
    		System.out.println(c); //50

The *IntContainer* class extends that Interface, so its instances can be used wherever a regular *int* could be. If it is placed in an expression where an *int* is expected, the instance itself is replaced by the result of its *intValue()* method.
