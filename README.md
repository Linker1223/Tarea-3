# Tarea-3
Gonzalez Aguilar Rene 18212190

## 1\. Define: Clase Base, Clase Derivada.

***Base**: Es por así llamarlo la clase principal de un programa, seria
la clase primaria sin incluir la clase main en donde se corre todo el
programa en si.*

***Derivada**: Son clases que dependen de las clases bases, ya que
algunos de sus métodos son también heredados, y muchas veces, el
compilador arrojara malos resultados, ya que al ser dependientes estas
clases, a veces podrán generar errores
lógicos.*

## 2\. Haz un diagrama UML donde se muestre la relación de herencia entre las  clases Figura, Recangulo y Circulo como vimos en clase.

## 3\. ¿Indica cuales son las clases base y las derivadas.

## 4\. ¿Que es herencia simple y herencia múltiple? ¿En c\# se puede hacer herencia múltiple?

***Simple:** Indica que se pueden definir nuevas clases solamente a
partir de una clase inicial.*

***Multiple:** Indica que se pueden definir nuevas clases a partir de
dos o más clases iniciales.*

*No, en c\# solo se permite la herencia
simple.*

## Escribe el programa de Figura como vimos en clase, donde agregues varios tipos de figuras a una lista y recorre la lista llamando a un método de las figuras, además:

*5.1 Se sobrecarguen los constructores y se acceda a los constructores
de la clase base.*

*5.2 Explica para que nos sirve la palabra base.*

*5.3 Haz el método Dibuja() que sea virtual y redefinelo en solo una de
las clases derivadas.*

``` 
using System; 
using System.Collections.Generic;

namespace Figura2 
{ 
  class Vector2d 
  { 
    public int x, y; 
    public Vector2d(int x, int y) 
    { 
        this.x=x; this.y=y; 
    } 
    public override string ToString() 
    { 
      return String.Format("{0},{1}", x, y); 
    }
  } 
  
  abstract class Figura 
  { 
    public Vector2d position; 
    public string fill, border;
    //Constructor por defecto 
    public Figura():this( new Vector2d(100, 100))
    {
    }
    //constructor de figura
    public Figura(Vector2d pos)
    {
      position= pos;
      fill= "white";
      border= "black";
    }
    public abstract void Dibuja();
  }

  class Circulo : Figura
  {
    private int radio;
    public Circulo(Vector2d pos, int radio):base(pos)
    {
       this.radio= radio;
    }
    public Circulo ():base()
    {
       this.radio= 10;
    }
    public override void Dibuja() 
    {
       Console.WriteLine("Se dibuja un circulo en {0} de color {1}", position, fill);
    }
  }

  class Rectangulo : Figura
  {
    public Rectangulo(Vector2d pos):base(pos)
    {
    }
    public Rectangulo ():base()
    {
    }

    public override void Dibuja() 
    {
        Console.WriteLine("Se dibuja un Rectangulo en {0} de color {1}", position, fill);
    }
  }
  //Figura Agregada
  class Triangulo : Figura
  {
    public Triangulo(Vector2d pos):base(pos)
    {
    }
    public Triangulo ():base()
    {
    }

    public override void Dibuja() 
    {
        Console.WriteLine("Se dibuja un Triangulo en {0} de color {1}", position, fill);
    }
  }
  class Program
  {
      static void Main(string[] args)
      {
  
          List<Figura> figuras = new List<Figura>();
          figuras.Add(new Circulo());
          figuras.Add(new Rectangulo(new Vector2d(200,200)));
          figuras.Add(new Triangulo(new Vector2d(120,150)));
          foreach(Figura f in figuras)
          f.Dibuja();
         
      }
  }
}
```
