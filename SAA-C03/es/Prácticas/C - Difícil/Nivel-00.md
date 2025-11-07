# 🥇 Nivel 00 — Difícil

Crea tu primera **VPC pública** y conéctate a un **servidor web** (HTTP). En modo **Difícil** solo se describe el problema y la solución esperada; no hay pasos ni parámetros concretos.

Se debe realizar tanto en **GUI** como en **CLI** **documentando todos los pasos** de manera similar a las prácticas de dificultad "Fácil" y comparar el resultado con estas (ya que vendrían a ser la solución).

## 🎯 Objetivo

Desplegar una red mínima en AWS que exponga un servidor web a Internet de forma segura y funcional.

## ✅ Solución esperada

Recursos creados con nombres coherentes, una **VPC pública** con una subred pública, salida a Internet mediante **Internet Gateway**, una **tabla de rutas pública** asociada a la subred, un **Security Group** que permita **HTTP**, y una **instancia EC2** que sirva una página web accesible desde Internet.

## 🗺️ Arquitectura objetivo (resultado final)

```mermaid
---
title: "Nivel 00 — Objetivo final"
---
graph BT

subgraph AWS[AWS]
    IGW[Internet Gateway]
    subgraph VPC["VPC-Publica"]
        RT["RT-Publica -> IGW"]
        subgraph SUB["subnet-pub-a"]
            EC2["EC2-WebPublica"]
            SG["SG-WebPublica"]
        end
    end
end

Internet[Internet]
PC[Tu ordenador]

IGW <--> VPC
RT --> SUB
SG ---> EC2
Internet --> IGW
PC -->|"GET / HTTP"| Internet
```

## 🔎 Verificación

Resultado esperado: acceder a `http://<IP_PUBLICA>` y obtener el mensaje de bienvenida servido por la instancia.

## 🧹 Limpieza

Borra todos los componentes usados en el orden adecuado.
