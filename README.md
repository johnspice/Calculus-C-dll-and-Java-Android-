# Calculusdll
Analizador sintáctico de funciones Matematicas

Esta librería está desarrollada en c#
Posee 4 métodos:

1.- Sintaxis (string fx, char var) ; este método tiene como parámetro  la función fx. Y la variable a evaluar var. Retorna  true si la sintaxis esta correcta y false si hay error en la sintaxis.
     Ejemplo de posible estructura admitida.
fx=”2*x+(sen(x))/(log(x))”
funciones admitidas
seno=sin(x)  ó sen(x) 
Asen=asn(x)
Acos=acs(x)
Atan=atn(x)
coseno= cos(x)
tangente=tan(x)
absoluto=abs(x)
logaritmo natural=Ln=log(x)
exponencial=e=exp(x)
raíz cuadrada =sqr(x)


2.- EvaluaFx(double x); 
     Retorna un doublé resultado de evaluar x en la función previamente declarada
     
3.- Dx(double x)
     Retorna double resultado de evaluar x en la función previamente declarada
     
4.- Integra(double LI, double LS ,double dx)
Retorna doublé resultado de integrar desde Li hasta LS con ancho de intervalo dx

