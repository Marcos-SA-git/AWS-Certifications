# 💎 Nivel 6 — Realista

**Asunto:** Unificar conectividad este-oeste entre VPCs con mínima disrupción y respetando rutas especiales existentes.  
**Contexto:** La organización opera **tres VPCs** (pública, privada, servicios). **S3** en la VPC privada debe continuar yendo por **Gateway Endpoint**. El servicio interno en VPC-Servicios se consume por **PrivateLink** desde VPC-Privada. Se solicita un diseño **hub-and-spoke** escalable.

## Requerimiento

- Implementar un **punto de tránsito** central entre VPCs manteniendo intactos los flujos **S3 por GWEP** y **PrivateLink**.  
- Asegurar que **todo tráfico entre CIDRs de las VPCs** fluya por el **hub** y **no** por Internet.

## Criterios de aceptación

- Existe un **Transit Gateway** con **attachments** a las tres VPCs y una **tabla de rutas** asociada con **propagación** activa.  
- Las **Route Tables** de cada VPC encaminan **CIDRs remotos → TGW** y preservan `Default → IGW/NAT` y `pl-S3 → GWEP`.  
- Desde una instancia en **VPC-Privada**:  
  - Acceso HTTP por **IP privada** a workloads en **VPC-Publica** y **VPC-Servicios**.  
  - Acceso a **S3** funciona aun si se **retira temporalmente** la ruta por defecto a NAT.  
  - Acceso por **PrivateLink** sigue operativo sin depender del TGW.  
- Se entrega **diagrama** y **registro de pruebas** (comandos y resultados).

## Entregables

- **Diagrama** de la topología con TGW (nombres de recursos y rutas clave).  
- **Resumen de decisiones** (attachments elegidos, tabla única vs múltiples tablas TGW).  
- **Evidencias** de pruebas (conexión entre VPCs, S3 por GWEP, PrivateLink).  
- **Plan de reversión**: eliminación ordenada de rutas hacia TGW, detención de propagación, borrado de attachments y del TGW.
