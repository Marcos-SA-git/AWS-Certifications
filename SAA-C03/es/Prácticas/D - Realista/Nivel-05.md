# 💎 Nivel 5 — Realista

**Asunto:** Minimizar exposición a Internet del tráfico hacia S3 desde entornos privados.  
**Contexto:** El equipo de seguridad exige que el acceso a **S3** desde **subnets privadas** no dependa de **NAT/IGW** y permanezca dentro de la red de **AWS**. Evitar cambios disruptivos en flujos actuales (el resto de tráfico debe continuar por NAT).

## Requerimiento

- Habilitar **acceso privado a S3** desde **VPC-Privada** empleando mecanismos nativos de red.  
- No modificar el comportamiento de salida a Internet para destinos **no S3**.  
- La solución debe ser **reversible** y cumplir principios de **mínimo cambio**.

## Criterios de aceptación

- Existe un **VPC Endpoint** tipo **Gateway** para **S3** en **VPC-Privada** y queda **asociado** a la(s) **tabla(s) de rutas** usada(s) por las **subnets privadas**.  
- En la **RT-Privada**, el tráfico a **S3** apunta al **Endpoint** mediante el **Prefix List** correspondiente, coexistiendo con `0.0.0.0/0 → NATGW` para el resto.  
- Desde una instancia en **subnet-priv-a**, la llamada a `http://s3.<region>.amazonaws.com` **funciona** aun cuando se **retira temporalmente** la ruta por defecto a **NAT**, mientras que `http://example.com` **falla** en ese estado.  
- Se devuelve un **rollback** documentado (eliminar el endpoint y restaurar rutas por defecto).  
- No se introducen permisos públicos en **S3** ni cambios de IAM fuera del alcance.

## Entregables

- **Diagrama** de arquitectura actualizada y **resumen de decisiones** (qué RTs se asociaron y por qué).  
- **Evidencias** (capturas o logs) de pruebas con y sin ruta por defecto a NAT.  
- **Plan de reversión** validado.
