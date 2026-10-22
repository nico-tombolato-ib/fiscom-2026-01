# Pregunta y predicciones

Completen este archivo **antes** de ejecutar los experimentos.

## Pregunta

¿Qué evidencia necesitamos para confiar en una trayectoria del oscilador calculada durante muchos ciclos?

Necesitamos verificar que el p, converge a uno. Es decir, verificar que el valor es muy cercano, y la variación de p entre un h y su mitad es cada vez menor.

## Modelo y supuestos

- Una masa unida a un resorte ideal, sin rozamiento: $m x''=-kx$.
- Medimos el tiempo en unidades de $1/\omega$, con $\omega=\sqrt{k/m}$. Así la ecuación queda $x''=-x$ y un período dura $2\pi$.
- La energía por unidad de masa es $E=(x^2+v^2)/2$.

## Predicciones

1. ¿Qué forma tiene la órbita exacta en el plano $(x,v)$? ¿Qué pasa con la energía exacta a lo largo del tiempo?

   * La energía debe permanecer constante. Por lo que, en este espacio de fases adimensional, la trayectoria debe ser una circunferencia de radio 1.

2. Escriban a mano un paso de Euler explícito para $x''=-x$. ¿En qué factor cambia $x^2+v^2$ en ese paso? ¿Y en un paso de Euler implícito?

   * **Euler explícito**:
      El resultado que queda es
      $$
         x_{n+1}=x_n+hv_n
      $$$$
         v_{n+1}=v_n-hx_n
      $$

      Luego la energía es $E_{n+1}=(x_n^2+v_n^2)(1+h^2)/2$

   * **Euler implícito**:
      El resultado que queda es
      $$
         x_{n+1}=x_n+hv_{n+1}
      $$$$
         v_{n+1}=v_n-hx_{n+1}
      $$
      Entonces
      $$
         x_{n+1}=\frac{x_n+hv_n}{1+h^2}
      $$$$
         v_{n+1}=\frac{v_n-hx_n}{1+h^2}
      $$

      Luego la energía es $E_{n+1}=(x_n^2+v_n^2)/[2(1+h^2)]$


3. Con esa cuenta, ¿qué esperan que pase con la amplitud y con el período de la oscilación después de diez períodos con cada método? ¿Qué verían en el plano $(x,v)$?

   Creo que se observará un aumento de radio en el espacio de fases para el **Euler explícito** y una reduccion del radio en el **Euler implícito**. Algo como espirales hacia afuera y hacia adentro respectivamente.

4. Si `dt` se reduce a la mitad, ¿qué esperan que ocurra con el error a tiempo final fijo?

   Vimos la clase pasada que **Euler explícito** tiene un error de orden **independiente de h**, mientras que **Euler implícito** tiene un error que va como $Ch^p$. Por lo que el error global del segundo método se reducirá mientras el del primero permanecerá constante.

5. Para el resorte, ¿cuántas iteraciones de Newton esperan que haga falta en cada paso implícito?

   Hace falta solo una iteración para que el método de Newton converja a la solución exacta dado que el sistema es lineal.

## Criterio de aceptación

Propongan un criterio para decidir si un valor de `dt` es aceptable para
simular cien períodos. ¿Qué cantidad medirían y qué tolerancia le pedirían?
