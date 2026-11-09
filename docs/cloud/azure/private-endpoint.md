---
title: "Private Endpoint"
date: "2026-11-09T13:50:00+01:00"
author: "Fco. Javier Cousiño"
categories:
  - "azure"
tags:
  - "Azure"
  - "Networking"
  - "Seguridad"
  - "Private Link"
description: "Azure Private Endpoint es una interfaz de red que proporciona conectividad privada y segura a servicios de Azure. Permite acceder a servicios como Storage, SQL Database, Cosmos DB y más desde una VNet sin exponerlos a internet público, mejorando la seguridad y cumplimiento normativo."
---

Azure **Private Endpoint** es una interfaz de red que proporciona conectividad privada y segura a servicios de Azure (Storage, SQL Database, Cosmos DB, etc.). Permite acceder a estos servicios desde una red virtual sin exponerlos a internet público.

## ¿Qué es Private Endpoint?

Private Endpoint es una característica de Azure que implementa el servicio **Azure Private Link**. Crea una conexión privada y dedicada entre tus aplicaciones y servicios de Azure dentro de tu [red virtual (VNet)](../../otro/conceptos-tecnicos.md#vnet-red-virtual-de-azure).

### Características principales:

- **Conectividad privada**: Acceso a servicios de Azure sin pasar por internet público
- **Seguridad mejorada**: Reduce la superficie de ataque eliminando exposición en internet
- **Cumplimiento normativo**: Ayuda a cumplir requisitos de residencia de datos y regulaciones
- **Mejor rendimiento**: Conexión directa dentro de la red de Microsoft
- **Control de acceso granular**: Usa [Grupos de Seguridad de Red (NSG)](../../otro/conceptos-tecnicos.md#nsg-grupo-de-seguridad-de-red) y [firewalls](../../otro/conceptos-tecnicos.md#firewall)
- **Integración con DNS privado**: Resolución de nombres dentro de la VNet

## Servicios que soportan Private Endpoint

Los siguientes servicios de Azure pueden ser accedidos a través de Private Endpoint:

| Servicio | Descripción |
|----------|-------------|
| **Azure Storage** | [Blob Storage](../../otro/conceptos-tecnicos.md#blob-storage), File Share, Table Storage, Queue Storage |
| **Azure SQL Database** | Base de datos relacional totalmente administrada |
| **Azure Cosmos DB** | Base de datos NoSQL distribuida globalmente |
| **Azure Key Vault** | Gestión de secretos y certificados |
| **Azure App Service** | Hosting de aplicaciones web y APIs |
| **Azure Container Registry** | Registro de imágenes de contenedores |
| **Azure Event Hubs** | Ingesta de eventos a escala |
| **Azure Service Bus** | Mensajería empresarial |
| **Azure Database for PostgreSQL/MySQL** | Bases de datos de código abierto |
| **Azure Backup** | Solución de copia de seguridad |

## Arquitectura de Private Endpoint

```
┌─────────────────────────────────────────────────────┐
│                   Azure (Cloud)                      │
│                                                     │
│  ┌──────────────────────────────────────────────┐  │
│  │          Red Virtual (VNet)                  │  │
│  │                                              │  │
│  │  ┌──────────────┐    ┌──────────────────┐  │  │
│  │  │  Máquina     │    │  Private         │  │  │
│  │  │  Virtual     │────│  Endpoint        │  │  │
│  │  │  (Cliente)   │    │  (Interfaz NIC)  │  │  │
│  │  └──────────────┘    └────────┬─────────┘  │  │
│  │                               │            │  │
│  │                         [IP Privada]       │  │
│  └───────────────────────────────┼────────────┘  │
│                                  │               │
│  ┌───────────────────────────────┼────────────┐  │
│  │  Servicio Azure                │            │  │
│  │  (Storage, SQL DB, etc)        │            │  │
│  │  ◄──────────────────────────────            │  │
│  └────────────────────────────────────────────┘  │
│                                                     │
└─────────────────────────────────────────────────────┘

        NO pasa por Internet Público
```

## Ventajas de usar Private Endpoint

### 🔒 Seguridad
- Elimina exposición de servicios en internet
- [Firewall](../../otro/conceptos-tecnicos.md#firewall) de Azure y NSG proporcionan control granular
- Cumple requisitos de seguridad estrictos

### 📊 Rendimiento
- Conexión directa dentro de la red de Microsoft
- Menor latencia y más estable que conexiones VPN
- Ancho de banda dedicado

### 📋 Cumplimiento normativo
- Residencia de datos garantizada
- Cumple HIPAA, GDPR, SOC 2, ISO 27001
- Auditabilidad mejorada

### 🎯 Control
- Gestión centralizada de acceso
- Políticas de firewall específicas por servicio
- [DNS](../../otro/conceptos-tecnicos.md#dns-sistema-de-nombres-de-dominio) privado integrado

## Comparación: Private Endpoint vs Service Endpoint vs VPN

| Característica | Private Endpoint | [Service Endpoint](../../otro/conceptos-tecnicos.md#service-endpoint) | [VPN](../../otro/conceptos-tecnicos.md#vpn-red-privada-virtual) |
|---|---|---|---|
| Conectividad | Privada dedicada | Ruta optimizada | Encriptada sobre internet |
| Exponido en internet | No | Sí | Depende |
| Complejidad | Media | Baja | Alta |
| Costo | Moderado | Bajo | Bajo-Moderado |
| Performance | Excelente | Bueno | Bueno |
| Casos de uso | Seguridad crítica | General | Acceso remoto |

## Creación de un Private Endpoint

### Requisitos previos:

- Una [Red Virtual (VNet) existente](../../otro/conceptos-tecnicos.md#vnet-red-virtual-de-azure)
- Acceso de administrador a la suscripción
- El servicio de Azure (Storage, SQL, etc.) ya creado

### Pasos básicos (Portal Azure):

1. **Navega al servicio** (p.ej., Storage Account)
2. **Networking** → **Private endpoint connections**
3. **Crear Private Endpoint**
4. Configura:
   - Nombre del endpoint
   - [Subred](../../otro/conceptos-tecnicos.md#subred) destino
   - Integración con DNS privado
5. **Revisar y crear**

### Ejemplo con PowerShell:

```powershell
# Crear Private Endpoint para Storage Account
$vnet = Get-AzVirtualNetwork -Name "miVNet" -ResourceGroupName "miRG"
$subnet = $vnet.Subnets[0]

$storage = Get-AzStorageAccount -Name "miStorage" -ResourceGroupName "miRG"

New-AzPrivateEndpoint `
  -Name "miStoragePE" `
  -ResourceGroupName "miRG" `
  -VirtualNetwork $vnet `
  -Subnet $subnet `
  -PrivateLinkServiceConnection (New-AzPrivateLinkServiceConnection `
    -Name "miStorageConnection" `
    -PrivateLinkServiceId $storage.Id `
    -GroupId "blob")
```

### Ejemplo con Azure CLI:

```bash
# Crear Private Endpoint para SQL Database
az network private-endpoint create \
  --name miSqlPE \
  --resource-group miRG \
  --vnet-name miVNet \
  --subnet miSubnet \
  --private-connection-resource-id /subscriptions/{subscriptionId}/resourceGroups/miRG/providers/Microsoft.Sql/servers/miSqlServer \
  --group-ids sqlServer \
  --connection-name miSqlConnection
```

## DNS Privado con Private Endpoint

Uno de los beneficios clave es la integración automática con **DNS privado**:

- El servicio resuelve automáticamente al IP privado de Private Endpoint
- Funciona transparentemente sin cambios en la aplicación
- Las aplicaciones usan el mismo nombre de dominio que en internet público

### Configuración de DNS privado:

```
Zona DNS privada: database.postgres.database.azure.com
Registro A: miDB.database.postgres.database.azure.com → 10.0.1.5 (IP privada)
```

Las aplicaciones en la VNet se conectan automáticamente a través del Private Endpoint sin cambios en la [cadena de conexión](../../otro/conceptos-tecnicos.md#uri-identificador-de-recurso-uniforme).

## Monitoreo y Troubleshooting

### Verificar estado del Private Endpoint:

```powershell
# Ver Private Endpoints en una VNet
Get-AzPrivateEndpoint -ResourceGroupName "miRG"

# Ver estado de conexión
Get-AzPrivateEndpointConnection -ResourceGroupName "miRG"
```

### Problemas comunes:

| Problema | Causa | Solución |
|----------|-------|----------|
| No puedo conectarme | [NSG](../../otro/conceptos-tecnicos.md#nsg-grupo-de-seguridad-de-red) bloqueando | Revisar reglas NSG |
| DNS no resuelve | DNS privado no configurado | Habilitar integración DNS privada |
| Alto latency | Mal placement de PE | Usar misma región que servicio |
| Conexión rechazada | Firewall del servicio | Permitir tráfico de VNet |

## Mejores prácticas

### ✅ Haz:

1. **Aisla servicios críticos** con Private Endpoints
2. **Usa DNS privado** para simplificar configuración
3. **Implementa [NSGs](../../otro/conceptos-tecnicos.md#nsg-grupo-de-seguridad-de-red) restrictivos** sobre permisivos
4. **Monitorea accesos** con Azure Monitor
5. **Documenta mapeo** de Private Endpoints a servicios
6. **Revisa regularmente** políticas de [firewall](../../otro/conceptos-tecnicos.md#firewall)

### ❌ No hagas:

1. No expongas servicios en internet si no es necesario
2. No olvides habilitar integración DNS privada
3. No uses reglas NSG demasiado amplias
4. No mezcles acceso público y privado sin justificación

## Casos de uso reales

### Caso 1: Datos sensibles
```
Aplicación interna → Private Endpoint → SQL Database (sin acceso internet)
```

### Caso 2: Cumplimiento normativo
```
Industria sanitaria → Private Endpoint → Storage (HIPAA compliant)
```

### Caso 3: Arquitectura multi-tier
```
Frontend (público) → Private Endpoint → Backend APIs
Backend APIs → Private Endpoint → Base de datos
```

## Costos

Azure Private Endpoint tiene costos asociados:

- **Horas de Private Endpoint activo**: ~$0.01 USD/hora
- **Datos procesados**: Incluido en los costos normales del servicio
- **Libre en tier**: Ciertos servicios incluyen endpoints gratis

**Estimación mensual**: Para 1 Private Endpoint activo 24/7 ≈ $7 USD/mes

Consulta los [precios actuales en el sitio de Azure](https://azure.microsoft.com/es-es/pricing/details/private-link/).

## Referencias

- [Documentación oficial de Azure Private Link](https://learn.microsoft.com/es-es/azure/private-link/private-link-overview)
- [Crear Private Endpoint en Azure Portal](https://learn.microsoft.com/es-es/azure/private-link/create-private-endpoint-portal)
- [Azure Private Link + DNS privado](https://learn.microsoft.com/es-es/azure/private-link/private-endpoint-overview)
- [Mejores prácticas de seguridad en Azure](https://learn.microsoft.com/es-es/azure/security/fundamentals/best-practices-and-patterns)
- [Azure Well-Architected Framework - Seguridad](https://learn.microsoft.com/es-es/azure/architecture/framework/security/)
