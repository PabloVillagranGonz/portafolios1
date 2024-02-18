# Portfolio

### Espectativas antes de aprender POO:
Mis espectativas del temario eran saber manejar bien la programación 
orientada a objetos y asi de esta manera mejorar a la hora de programar.

Tener un buen conocimiento sobre este tema te ayuda a la hora de mejorar
una aplicación.
Es mas sencillo cambiar o modificar el codigo con esta orientación.
### Cosas aprendidas en las dos unidades:

- Saber asociar entre clases
- Notación UML
- Relaciones: composición y agregación



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

### Conclusiones
