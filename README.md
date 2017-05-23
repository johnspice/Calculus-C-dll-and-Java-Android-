# Calculusdll
Analizador sintáctico de funciones Matematicas

Esta librería está desarrollada en c#
Posee 4 métodos:

### 1. Sintaxis (string fx, char var)
     este método tiene como parámetro  la función fx. Y la variable a evaluar var. Retorna  true si la sintaxis esta correcta y false si      hay error en la sintaxis.
     Ejemplo de posible estructura admitida.
     fx=”2*x+(sen(x))/(log(x))”

#### funciones admitidas
1. seno=sin(x)  ó sen(x) 
2. Asen=asn(x)
3. Acos=acs(x)
4. Atan=atn(x)
5. coseno= cos(x)
6. tangente=tan(x)
7. absoluto=abs(x)
8. logaritmo natural=Ln=log(x)
9. exponencial=e=exp(x)
10. raíz cuadrada =sqr(x)

Nota="es importante colocar los * para las multiplicaciones"


### 2. EvaluaFx(double x)
     Retorna un doublé resultado de evaluar x en la función previamente declarada
     
### 3. Dx(double x)
     Retorna double resultado de evaluar x en la derivada de la función previamente declarada
     
### 4. Integra(double LI, double LS ,double dx)
    Retorna doublé resultado de integrar desde Li=limite inferior hasta LS=limite superior con ancho de intervalo "dx"


## como usar en Proyecto


1. download Calculus.dll
2. Add/Reference /Calculus.dll        
3. añadimos "using Calculus;" 
4. construir objeto calculus. ejemplo para consola;


          double fx,area;
            Calculo AnalizadorDeFunciones = new Calculo();

            if (AnalizadorDeFunciones.Sintaxis("2*x+2", 'x')) //pasamos la funcion con la variable a evaluar
            {
                fx = AnalizadorDeFunciones.EvaluaFx(2.3); 
                area= AnalizadorDeFunciones.Integra(2,5,0.0003);
                        
                Console.WriteLine("f(2.3)={0}    Area={1}", fx,area);
                
            }
            else{
               // aquí mensaje de error en sintaxis
            }
            
link youtube muestra su funcionamiento dentro de visualc# en un WindowsForms.
1. https://www.youtube.com/watch?v=isje1E_JCLY
