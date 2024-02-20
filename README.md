# Portfolio

![Imagen portfolio](C:\Users\alumnoDAM\Downloads\descarga.png)

### Espectativas antes de aprender POO:
Mis espectativas del temario eran saber manejar bien la programación 
orientada a objetos y asi de esta manera mejorar a la hora de programar.

Tener un buen conocimiento sobre este tema te ayuda a la hora de mejorar
una aplicación. Es mas sencillo cambiar o modificar el codigo con esta orientación.

Con los conocimientos adquiridos tenemos gran una gran parte ya hecha, ahora
hace falta practicar y zanjarlos.

### Cosas aprendidas en las dos unidades:

- Asociación entre clases
- Propiedades de la POO
- This
- Paso por valor o referencia
- Metodos get y set
- Constructores
- Relaciones: composición y agregación
- Notación UML
- Herencia y reglas de  visibilidad
- Clases abstractas
- Clase object
- Metodo equals


Tambien una ayuda muy buena es la pagina web que tiene jorge
ya que hay apuntes sobre lo que damos:

##### [Apuntes Jorge Sanzhez](https://jorgesanchez.net/gbd)

### Ejercicios mas importantes:  
1. Ejercicio 1:

* En esta primera parte creamos la clase Coche.
```java
public class Coche {
    protected double velocidad;
    protected double combustible;

    public Coche(double combustible){
        this.combustible = combustible;
        this.velocidad = 0;
    }

    public double getVelocidad() {
        return velocidad;
    }

    public double getCombustible() {
        return combustible;
    }

    public void acelerar(double incremento){
        this.velocidad  += incremento;
        combustible--;
    }

    public void frenar(double decremento){
        this.velocidad -= decremento;
    }

    public void escribir(){
        System.out.println("velocidad: " + this.velocidad + ", " + "combustible: " + this.combustible);
    }
}
```
* En esta segunda parte vamos a crear la clase CocheVolador
```java
public class CocheVolador extends Coche{
    protected double altura;

    public CocheVolador(double combustible){
        super(combustible);
        this.altura = 0;
    }

    public void setAltura(double altura) {
        this.altura = altura;
    }
    public void escribir(){
        System.out.println("Velocidad :" + this.velocidad + (", ") + ("combustible : " + this.combustible) + (", ") + ("altura :" + this.altura));
    }
}
```
* Y para finalizar, crearemos la App.
```java
public class AppCoche {
    public static void main (String[] args) {
        Coche c1 = new Coche(40);
        CocheVolador v1 = new CocheVolador(50);

        c1.acelerar(5);
        c1.acelerar(10);
        c1.escribir();

        v1.acelerar(5);
        v1.acelerar(10);
        v1.escribir();

        //CocheVolador v2 = c1;
        Coche c3 = v1;
        c3.acelerar(25);
        v1.escribir();

        v1.setAltura(50);
        v1.escribir();

        c3.escribir();

        ((CocheVolador)c3).setAltura(60);//funciona ya que señala a un objeto volador
        v1.escribir();

        ((CocheVolador)c1).setAltura(20);//error porque no señala a un objeto volador

    }
}

```

2. Ejercicio 2:
```java
public class Cuadrado implements Escribible, Dibujable{

    public Punto punto;
    public double lado;
    public Cuadrado (Punto punto, double lado){
        this.punto = punto;
        this.lado = lado;
    }

    @Override
    public void escribir() {
        System.out.println("Coordenadas de la esquina izquierda: " + this.punto.x + ", " +
                            this.punto.y + ", tamaño del lado " + this.lado);
    }
    @Override
    public void dibujar() {
        for (int i = 1; i <= lado ; i++) {
            for (int j = 1; j <= lado ; j++) {
                System.out.print("* ");
            }
            System.out.println();
        }
    }
}
```

```java
public class Punto implements Escribible {
    public double x;
    public double y;
    public Punto (double x, double y){
        this.x = x;
        this.y = y;
    }
    public Punto(){
        this(0,0);
    }
    public void cambiar(double x, double y){
        this.x = x;
        this.y = y;
    }

    @Override
    public void escribir() {
        System.out.println("(" + x + (", ") + y + (")"));
    }
}
```

```java
public interface Escribible {
    void escribir();

}
``` 

```java
public interface Dibujable {
    public void dibujar();
}
```

```java
public class App {
    public static void main(String[] args) {
        Punto p = new Punto(5, 10);
        Punto q = new Punto(-4, 9);
        Cuadrado c = new Cuadrado(p, 10);

        Escribible e;
        e = p;
        e.escribir();
        e = q;
        e.escribir();
        e = c;
        e.escribir();
        c.dibujar();

        Escribible [] array = new Escribible[4];
        array[0]=p;
        array[1]=q;
        array[2]=c;
        array[3]= new Cuadrado(new Punto(3,4),20);
        for (Escribible esc: array) {
            esc.escribir();
        }

    }
}
```


### Conclusiones

Hemos aprendido a saber utilizar los objetos y las clases, las propiedades
de la programación orientada a objetos, todos los metodos y constructores, 
las relaciones y la herencia.

Lo que mas me ha gustado han sido las interfaces, ya que son sencillas de crear
basta que no hace falta implementar metodos.
Es una clase abstracta y solo sirve para definir como tiene que funcionar
una clase.

Lo que menos me ha gustado, o me ha costado más de entender, fueron las
relaciones de agregación y composición y los métodos estáticos. Me costo
de entender ya que no entendia bien para lo que servía.

La utilidad que veo es que gracias a esto podemos tener un código reutilizable,
organizado y muy facil de mantener. 

Permitiendo trabajar en equipo, la facilidad a la hora de tener y 
corregir errores, y nos permite construir sistemas mas complejos y 
de forma mas sencilla y organizada.