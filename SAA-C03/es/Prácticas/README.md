# 🎮 PARTE PRÁCTICA

## 🧭 Introducción

¡Bienvenido a la parte práctica del temario!

Estas prácticas están diseñadas para ofrecerte una progresión intuitiva, escalonada y totalmente aplicada de los conceptos vistos en la teoría.  
Su objetivo es ayudarte a integrar el conocimiento técnico con la resolución práctica de escenarios reales, tal y como exige la certificación AWS.

Por ello, las prácticas comienzan con uno de los servicios más esenciales y característicos de AWS: **VPC + EC2**, y a partir de ahí se va construyendo el resto del contenido de red, seguridad y servicios gestionados.

> 🗒️ **Nota**: el orden de las prácticas no sigue exactamente la secuencia teórica, ya que se prioriza la construcción lógica de una arquitectura completa. Por lo que **se recomienda** haber completado hasta el apartado *Nº 4. EC2 - Elastic Compute Cloud* de la parte teórica para comenzar con las prácticas.

## ⚙️ ¿Cómo funcionan?

Las prácticas se conciben como un **modo campaña o videojuego de aprendizaje**.  
Cada **nivel** amplía y refuerza lo aprendido en los anteriores, formando una red de conocimientos interconectados.  

Además, puedes elegir la **dificultad** según tu nivel de experiencia o tu objetivo de práctica:

| Dificultad | Descripción |
|-------------|-------------|
| 🟢 **Fácil (F)** 🥉 | Práctica totalmente guiada, con pasos detallados, comandos y resultados esperados. Ideal para tu primer contacto con el tema. |
| 🟡 **Media (M)** 🥈 | Instrucciones parciales y esquemas visuales; tú decides cómo avanzar. Perfecta para afianzar comprensión. |
| 🔴 **Difícil (D)** 🥇 | Solo incluye el contexto, un esquema final y los objetivos. Pensada para estudiantes que ya dominan el entorno. |
| ⚫ **Realista (R)** 💎 | Simulación profesional o de examen. Texto tipo cliente, ambigüedades intencionadas y cero instrucciones paso a paso. |

### 🧠 Sobre los modos Realista y el nivel final

Los primeros niveles de cada tema (X0–X4) están pensados para **dominar los fundamentos** y no incluyen versión Realista, ya que no aportaría valor práctico repetir configuraciones básicas sin guía.

A partir del **Nivel 5**, el modo **Realista (💎)** empieza a tener sentido: los escenarios se vuelven más complejos, hay múltiples caminos posibles y debes analizar qué enfoque es el más adecuado (coste, seguridad, rendimiento o escalabilidad).

Finalmente, **cada X niveles ⛳** encontrarás el *miniboss final* del bloque: una simulación completa en la que tendrás que diseñar e implementar una arquitectura AWS desde cero aplicando todo lo aprendido.  
No hay instrucciones detalladas, solo un contexto real y un objetivo. Tu éxito dependerá de tu criterio técnico.

Para que no te sientas tentado a mirar, encontrarás las soluciones a los niveles finales en otra carpeta separada. No encontrarás enlaces directos a la solución para que así te centres en aplicar **tu propia respuesta**.

Desde luego, puedes apoyarte en herramientas como ChatGPT para resolver dudas o comprobar conceptos, pero recuerda que hay empresas en donde su uso está restringido, y no tendrás acceso a ellas durante el examen oficial. Por ello, se recomienda limitar su uso si tu objetivo es practicar de forma auténtica y medir tu verdadero nivel.

### 🧩 Perfil híbrido y continuidad entre bloques

Cada bloque de niveles funciona como un nuevo “capítulo” de tu camino.  
Superar un *miniboss* no significa empezar desde cero, sino **evolucionar la misma arquitectura hacia un nuevo enfoque** (cómputo, almacenamiento, seguridad, automatización…).

Como aún no se ha introducido el uso de Terraform o IaC, encontrarás un **script CLI de restauración** que te permitirá levantar rápidamente la infraestructura base y continuar con el nuevo bloque sin perder tiempo ni contexto.  
Así podrás mantener una progresión coherente y seguir aprendiendo en profundidad sin preocuparte por reconstruir manualmente todo el entorno.

Alternativamente dentro de cada práctica podrás encontrar versiones donde se haga desde la interfaz web (GUI) o desde la terminal (CLI). De esta manera podrás dominar ambos terrenos. Aunque recomendamos que hagas cada miniboss con CLI para que puedas replicar rápidamente esos entornos como IaC.

> 🗨️ **Consejo**: completa primero cada nivel en modo **Fácil**, y vuelve luego en **Modos Difícil o Realista** para consolidar tus habilidades. El modo **Medio** es mejor para los que ya tienen un poco de experiencia en AWS o se ven con agallas para saltarse el modo fácil. ¿Te atreverás?

## 🪧 Índice de niveles

> 🚀 *Cada nivel se construye sobre el anterior, combinando teoría, práctica y visualización hasta formar una arquitectura completa y segura dentro de AWS.*

| Bloque | Nivel | Descripción | Dificultades |
|:-------|:------|:------------|:-------------|
| **Bloque 1: Redes y conectividad (VPCs)** | **Nivel 0** | Crea tu primera **VPC pública** y conéctate a un **servidor web**. | [F](./Fácil/Nivel-0.md) · [M](./Medio/Nivel-0.md) · [D](./Difícil/Nivel-0.md) |
| | **Nivel 1** | Crea una **VPC privada**, establece un **VPC Peering** y comprueba su **bidireccionalidad**. | [F](./Fácil/Nivel-1.md) · [M](./Medio/Nivel-1.md) · [D](./Difícil/Nivel-1.md) |
| | **Nivel 2** | Configura un **NAT Gateway** y proporciona **salida a Internet** a instancias privadas. | [F](./Fácil/Nivel-2.md) · [M](./Medio/Nivel-2.md) · [D](./Difícil/Nivel-2.md) |
| | **Nivel 3** | Crea una **tercera VPC** y conecta servicios mediante un **Interface Endpoint (PrivateLink)**. | [F](./Fácil/Nivel-3.md) · [M](./Medio/Nivel-3.md) · [D](./Difícil/Nivel-3.md) |
| | **Nivel 4** | Compara **VPC Peering vs PrivateLink** mediante trazas (`traceroute`) y rutas controladas. | [F](./Fácil/Nivel-4.md) · [M](./Medio/Nivel-4.md) · [D](./Difícil/Nivel-4.md) |
| | **Nivel 5** | Implementa un **Gateway Endpoint** para acceder a **S3 sin salir de AWS**. | [F](./Fácil/Nivel-5.md) · [M](./Medio/Nivel-5.md) · [D](./Difícil/Nivel-5.md) · [R](./Realista/Nivel-5.md) |
| | **Nivel 6** | Diseña una **VPC transitiva** y analiza el **flujo de tráfico entre redes**. | [F](./Fácil/Nivel-6.md) · [M](./Medio/Nivel-6.md) · [D](./Difícil/Nivel-6.md) · [R](./Realista/Nivel-6.md) |
| | **Nivel 7** | Crea una **cuarta VPC** con **DHCP Option Set** y personaliza su dominio interno. | [F](./Fácil/Nivel-7.md) · [M](./Medio/Nivel-7.md) · [D](./Difícil/Nivel-7.md) · [R](./Realista/Nivel-7.md) |
| | **Nivel 8** | Aplica **NACLs y Security Groups** para controlar y auditar el tráfico. | [F](./Fácil/Nivel-8.md) · [M](./Medio/Nivel-8.md) · [D](./Difícil/Nivel-8.md) · [R](./Realista/Nivel-8.md) |
| | **Nivel 9** | Integra todo lo anterior en una **arquitectura multi-VPC completa**. | [F](./Fácil/Nivel-9.md) · [M](./Medio/Nivel-9.md) · [D](./Difícil/Nivel-9.md) · [R](./Realista/Nivel-9.md) |
| | **Nivel 10** ⛳ | ??? | [R](./Realista/Nivel-10.md) |
| **Bloque 2: Cómputo (EC2)** | **Nivel 0** | Descripción del nivel | [F](./Fácil/Nivel-11.md) · [M](./Medio/Nivel-11.md) · [D](./Difícil/Nivel-11.md) |
| | **Nivel 11** | Descripción del nivel | [F](./Fácil/Nivel-11.md) · [M](./Medio/Nivel-11.md) · [D](./Difícil/Nivel-11.md) |