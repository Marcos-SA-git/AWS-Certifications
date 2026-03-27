# 🥇 Nivel 1 — Difícil

Crea una **VPC privada**, establece un **VPC Peering** con tu **VPC pública existente** y **comprueba su bidireccionalidad**. En modo **Difícil** solo se describe el problema y la solución esperada; no hay pasos ni parámetros concretos.

Se debe realizar tanto en **GUI** como en **CLI** **documentando todos los pasos** de manera similar a las prácticas de dificultad "Fácil" y comparar el resultado con estas (ya que vendrían a ser la solución).

## 🎯 Objetivo

Partiendo del resultado del **Nivel 00**, desplegar una **VPC privada** (sin salida directa a Internet) y conectarla con la **VPC pública** mediante **VPC Peering**, habilitando **enrutamiento en ambos sentidos** para tráfico por **IPs privadas**.

## ✅ Solución esperada

- Recursos creados con nombres coherentes.
- **VPC-Privada** con **subnet privada** y **RT-Privada** (sin ruta a Internet).
- **VPC Peering** entre ambas VPC y **rutas recíprocas** (cada RT apunta a la red de la otra VPC vía PCX).
- **Security Group** en la VPC privada que permita, como mínimo, **ICMP** desde la red de la VPC pública.
- **Instancias EC2** alcanzables **por IP privada** entre VPCs (bidireccionalidad).

## 🗺️ Arquitectura objetivo (resultado final)

```mermaid
---
title: "Nivel 1 — Objetivo final"
---
graph BT

subgraph AWS[AWS]
    subgraph VPC1["VPC-Publica"]
        IGW[IGW-Publica]
        RT1["RT-Publica<br>0.0.0.0/0 -> IGW<br>RUTA a VPC-Privada -> PCX"]
        subgraph SUB1["subnet-pub-a"]
            EC2PUB["EC2-WebPublica<br>IP privada 10.0.1.x"]
            SGPUB["SG-WebPublica"]
        end
    end

    subgraph VPC2["VPC-Privada"]
        RT2["RT-Privada<br>RUTA a VPC-Publica -> PCX"]
        subgraph SUB2["subnet-priv-a"]
            EC2PRI["EC2-Privada<br>Sin IP pública<br>IP privada 10.1.1.x"]
            SGPRI["SG-Privada<br>IN ICMP desde VPC-Publica<br>OUT all"]
        end
    end

    PCX["PCX-Publica-Privada"]
end

IGW --> VPC1
RT1 --> SUB1
RT2 --> SUB2
PCX --- VPC1
PCX --- VPC2
```

## 🔎 Verificación

- Acceso **por IP privada** entre instancias en ambas VPC (por ejemplo, **ICMP** de `EC2-WebPublica` a `EC2-Privada` con respuesta).
- La **VPC-Privada** permanece **sin salida directa a Internet**.

## 🧹 Limpieza

Borra los componentes creados en orden seguro: quita **rutas del PCX** en ambas RT → elimina el **PCX** → termina la **instancia privada** → borra **SG-Privada**, **RT-Privada**, **subnet-priv-a** y **VPC-Privada**.
