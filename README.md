# TechFTTH 🗺

**Sistema GIS de gestión para redes FTTH, ADSL y Wireless**

Desarrollado para **Empresas y Cooperativas proveedoras de servicios de internet** 

[![Demo en YouTube](https://img.shields.io/badge/▶_Ver_demo-YouTube-red)](https://youtu.be/prZgfUD74zA)
[![Python](https://img.shields.io/badge/Python-3.10+-blue)](https://python.org)
[![License](https://img.shields.io/badge/Licencia-MIT-green)](#licencia)

---

## ¿Qué es?

TechFTTH es una herramienta de escritorio que permite a operadores e ISPs 
gestionar visualmente su red de internet sobre un mapa real. Sin servidores, 
sin licencias, sin dependencias en la nube. Corre desde cualquier PC con Python.

Está pensada para cooperativas e ISPs pequeños que necesitan:
- Documentar su infraestructura física sobre cartografía real
- Diagnosticar fallas sin recorrer el tendido
- Capacitar operadores sin experiencia técnica previa

<img width="1366" height="768" alt="TechFTTH_v5" src="https://github.com/user-attachments/assets/4414bb8b-b2c3-40dc-8494-024759a90fd3" />

---

## Demo

[▶ Ver demo en YouTube — 1 minuto](https://youtu.be/prZgfUD74zA)

---

## Funcionalidades

### 🗺 Editor GIS de red
- Mapa real sobre OpenStreetMap
- 7 tipos de elementos: postes, clientes, CTOs, OLTs, antenas, fibra, wireless
- Snap automático a nodos al trazar tendido
- Undo/Redo de 50 pasos
- Propiedades editables por elemento

### 🔬 Diagnóstico de fallas
- Diagnóstico individual por cliente (algoritmo BFS)
- Correlación de fallas: rankea tramos por cantidad de clientes afectados
- Escaneo completo de red con informe de problemas
- Soporte para FTTH, ADSL y Wireless con modelos de atenuación específicos

### 🔧 Pruebas técnicas
- Estimación de potencia óptica (pérdida por fibra + splitter + conectores)
- Modelo ITU G.992.5 para ADSL (degradación por distancia)
- Cálculo FSPL para enlaces wireless (fórmula de Friis)

### 📋 Dashboard
- Estado general de la red en tiempo real
- Alertas activas: cortes, saturaciones, clientes sin nodo
- Ocupación de CTOs con semáforo de colores
- Referencia de datos operativos del ISP

### 🔌 Integración
- Consola SSH integrada con OLTs Huawei (MA5800-X7 / MA5608T) "adaptable a cualquier sistema / hardware"
- Alta y baja de ONUs desde la interfaz
- Modo Demo: simulador de OLT Huawei sin equipo real
- Importar clientes desde Excel
- Exportar a Excel completo y CSV para facturación

---

## Arquitectura
```
TechFTTH (HMI)          →  network.json (base de datos local)
     ↓                           ↓
SSH + Paramiko           →  OLT Huawei (RTU)
Excel / CSV              →  Sistema de facturación
OpenStreetMap tiles      →  Cartografía real
```

Conceptualmente equivalente a un sistema SCADA simplificado:
la OLT es el RTU, SSH es el protocolo de campo, 
y network.json es el historian.

---

## Stack técnico

| Componente | Tecnología |
|---|---|
| Interfaz gráfica | Python Tkinter + customtkinter |
| Mapa | tkintermapview + OpenStreetMap |
| Datos de red | JSON (portable, sin servidor) |
| Comunicación OLT | SSH vía Paramiko |
| Importación/exportación | openpyxl (Excel) |
| Algoritmo de diagnóstico | BFS sobre grafo de red |
| Modelos de atenuación | GPON / ITU G.992.5 / Friis |

---

## Capturas

<img width="1359" height="768" alt="Solapa_INSTALACIONES_cliente" src="https://github.com/user-attachments/assets/0c4bc905-8f63-424d-b54b-87687d4d919f" />

<img width="1359" height="768" alt="Solapa_INSTALACIONES_fibra" src="https://github.com/user-attachments/assets/4355161a-ac91-4df6-a2ad-e2196851f1a5" />

<img width="1359" height="768" alt="Solapa_INSTALACIONES_poste" src="https://github.com/user-attachments/assets/b6a739bc-07be-4c21-b59b-9e7073e3f79c" />

<img width="1359" height="768" alt="Solapa_PRUEBAS" src="https://github.com/user-attachments/assets/f24f080b-cef2-4544-bb52-37489b4de67d" />

<img width="1359" height="768" alt="Solapa_INTEGRACION_cliente" src="https://github.com/user-attachments/assets/7ab0de6a-0e91-4011-9e05-e46952833de4" />

<img width="1359" height="768" alt="Solapa_DIAGNOSTICO_problemas" src="https://github.com/user-attachments/assets/0a018fea-4e50-4b00-9579-b58a5352d444" />

<img width="1359" height="768" alt="Solapa_DIAGNOSTICO_moraPAGO" src="https://github.com/user-attachments/assets/8b3ea4bb-bb2e-443f-a749-1da64738e373" />

<img width="1359" height="768" alt="Solapa_DIAGNOSTICO_fibraINACTIVO" src="https://github.com/user-attachments/assets/71866906-f646-43f3-9355-c0e6c7dd601e" />

<img width="1359" height="768" alt="Solapa_DIAGNOSTICO_correlacion" src="https://github.com/user-attachments/assets/f6d0b506-8fde-4266-8b69-b977fc302fbc" />

<img width="1359" height="768" alt="solapa_DASHBOARD" src="https://github.com/user-attachments/assets/d70b63d2-65c3-410d-8a35-0323984a5672" />

---

## Contexto

Desarrollado para **Empresas y Cooperativas proveedoras de servicios de internet**
El objetivo principal fue darle a los operadores que no tienen 
formación técnica en redes, una herramienta visual que les permita localizar 
fallas, documentar instalaciones y gestionar la red sin depender de la CLI 
de la OLT para las operaciones cotidianas.

---

## Autor

prof.martintorres@educ.ar — ETI Patagonia  

---

