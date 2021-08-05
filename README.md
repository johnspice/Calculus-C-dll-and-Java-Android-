# Calculus lybrary for C#(dll) and Android(.aar) 
Analizador sintáctico de funciones Matematicas

Esta librería está desarrollada en c# tambien en JAVA(para Android)
Posee 4 métodos:
## Calculus C#
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


### como usar en Proyecto


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

## Calculus java Android
### Gradle
add in build.gradle(:app) 

     repositories {
          maven {
               url "https://dl.cloudsmith.io/public/troysoft/jplot/maven/"
          }
     }

     dependencies {
          implementation 'com.gabrielopez.plot:jplot:1.7'
     }


### Evaluar expresión sin variables 
crea un objeto MatFuncion

        MatFuncion fx=new MatFuncion("2+34-cos(0)+sqr(4)");
        double res;
        if(fx.CheckSintaxis()){
        // este if es necesario ya que si la expresión esta mal podría provocar un bloqueo ANR.
            res=fx.Resultado();
            Toast.makeText(this,"resultado = "+res,Toast.LENGTH_LONG).show();
        }
        else{
            Toast.makeText(this,"error en sintaxis",Toast.LENGTH_LONG).show();
        }

### Evaluar expresión con 1 variable
        
         MatFuncion fx=new MatFuncion("x*[2+x+sqr(x)]");
         double res;
        if(fx.CheckSintaxis()){
            fx.EvaluaEn('x',4);
            res=fx.Resultado();
            Toast.makeText(this,"resultado = "+res,Toast.LENGTH_LONG).show();

        }

        else{
            Toast.makeText(this,"error en sintaxis",Toast.LENGTH_LONG).show();
        }
### Evalúa expresión multivariables

        MatFuncion fx=new MatFuncion("x*[2+x+sqr(x)]+c+y^2");
        double res;
        if(fx.CheckSintaxis()){

            fx.EvaluaEn('x',4);
            fx.EvaluaEn('c',-2);
            fx.EvaluaEn('y',3);
            res=fx.Resultado();
            Toast.makeText(this,"resultado = "+res,Toast.LENGTH_LONG).show();

        }

        else{
            Toast.makeText(this,"error en sintaxis",Toast.LENGTH_LONG).show();
        }

### Metodos Públicos de la clase MatFuncion

* public  MatFuncion(String f): es el constructor acepta una cadena String con la expresión matemática a evaluar 
* public boolean CheckSintaxis(): evalúa la sintaxis de la función pasada en el constructor retorna un true si la sintaxis es correcta y un false si la sintaxis tiene algun error. 
* public void EvaluaEn(char var,double value): se llama a este método si hay variables en la expresión se pasa un Char(la variable) un double(el valor de la variable). puede llamarse a este método tantas veces como variables se tengan.  
* public double Resultado(): devuelve(un double) el resultado de evaluar la expresión ya sustituidos los valores de la variable o de las variables. 


