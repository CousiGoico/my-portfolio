# Azure Virtual Network (VNet)

## 📌 Resumen

- **Dificultad**: Intermedio
- **Tiempo de lectura**: 12 minutos
- **Categoría**: Azure Cloud
- **Última actualización**: 2024

## Introducción

**[Azure Virtual Network (VNet)](../../otro/conceptos-tecnicos.md#vnet-red-virtual-de-azure)** es el bloque fundamental de construcción para tu red privada en Microsoft Azure. Es un servicio de red que te permite conectar recursos de Azure entre sí, con usuarios locales y con internet. Una VNet es análoga a una red tradicional que operarías en tu centro de datos, pero con los beneficios adicionales de la infraestructura de escalabilidad, disponibilidad y aislamiento de Azure.

Una VNet te proporciona control total sobre tu espacio de direcciones IP, configuración de DNS, directivas de seguridad y enrutamiento de tráfico.

## Conceptos Fundamentales

### ¿Qué es una VNet?

Una [Virtual Network](../../otro/conceptos-tecnicos.md#vnet-red-virtual-de-azure) es una red aislada en Azure que actúa como un perímetro de seguridad para tus recursos. Cada VNet:

- Tiene un espacio de direcciones IP único
- Está aislada de otras VNets de forma predeterminada
- Puede subdividirse en subredes
- Puede conectarse a otras redes (locales o en la nube)
- Proporciona seguridad a través de Network Security Groups (NSGs)

### Componentes Principales

#### 1. **Espacio de Direcciones**
Es el rango de direcciones IP privadas que defines para tu VNet. Por ejemplo: `10.0.0.0/16` que proporciona 65,536 direcciones IP disponibles.

Puntos clave:
- Debe ser un rango de CIDR válido
- Pueden ser direcciones privadas (RFC 1918):
  - `10.0.0.0/8` (10.0.0.0 - 10.255.255.255)
  - `172.16.0.0/12` (172.16.0.0 - 172.31.255.255)
  - `192.168.0.0/16` (192.168.0.0 - 192.168.255.255)

#### 2. **Subredes**
Son segmentos del espacio de direcciones de una VNet. Cada subred tiene su propio rango CIDR dentro del espacio de direcciones de la VNet.

Características:
- Obligatorias para desplegar recursos en una VNet
- Cada recurso de Azure se debe desplegar en una subred específica
- Pueden tener diferentes configuraciones de seguridad (NSGs)
- Se pueden usar para segregación de recursos por función o entorno

#### 3. **[Network Security Groups (NSGs)](../../otro/conceptos-tecnicos.md#nsg-grupo-de-seguridad-de-red)**
Son conjuntos de reglas de [firewall](../../otro/conceptos-tecnicos.md#firewall) que controlan el tráfico de entrada y salida.

Propiedades:
- Se pueden aplicar a subredes o interfaces de red (NICs)
- Contienen reglas de entrada y salida
- Las reglas se evalúan por prioridad (0-65535)
- Permiten o deniegan tráfico basado en protocolos, puertos y direcciones IP

#### 4. **Interfaces de Red (NICs)**
Son las conexiones virtuales de las [máquinas virtuales](../../otro/conceptos-tecnicos.md#virtual-machine-vm) a la red. Cada NIC:
- Tiene una dirección IP privada
- Opcionalmente puede tener una dirección IP pública
- Está asociada a un NSG
- Puede tener múltiples direcciones IP (secundarias)

## Arquitectura de VNet

### Estructura Típica

```
┌─────────────────────────────────────────────────────────────┐
│                     Azure Virtual Network                    │
│                    (10.0.0.0/16)                             │
│                                                               │
│  ┌──────────────────────┐    ┌──────────────────────┐        │
│  │  Subred Frontend      │    │  Subred Backend      │        │
│  │  (10.0.1.0/24)       │    │  (10.0.2.0/24)       │        │
│  │                      │    │                      │        │
│  │ ┌──────────────────┐ │    │ ┌──────────────────┐ │        │
│  │ │  Web Servers     │ │    │ │  App Servers     │ │        │
│  │ │  VM1 VM2         │ │    │ │  VM3 VM4         │ │        │
│  │ └──────────────────┘ │    │ └──────────────────┘ │        │
│  │  NSG: Allow HTTP(80) │    │  NSG: Allow 3306    │        │
│  │                      │    │  (only from FE)     │        │
│  └──────────────────────┘    └──────────────────────┘        │
│                                                               │
│  ┌────────────────────────────────────────────────┐          │
│  │     Subred Database (10.0.3.0/24)              │          │
│  │  ┌────────────────────────────────────────┐   │          │
│  │  │  Database Server                        │   │          │
│  │  │  (Azure Database for MySQL)             │   │          │
│  │  └────────────────────────────────────────┘   │          │
│  │  NSG: Allow 3306 (only from Backend)         │          │
│  └────────────────────────────────────────────────┘          │
└─────────────────────────────────────────────────────────────┘
```

## Características Principales

### 1. Aislamiento de Red
- Las VNets están completamente aisladas por defecto
- El tráfico entre VNets debe ser explícitamente permitido
- Segmentación lógica de recursos por departamento, proyecto o entorno

### 2. Control de Tráfico
Con [NSGs](../../otro/conceptos-tecnicos.md#nsg-grupo-de-seguridad-de-red) puedes:
- Permitir o denegar tráfico específico
- Filtrar por protocolo (TCP, UDP, ICMP)
- Filtrar por puertos
- Filtrar por direcciones IP de origen y destino
- Aplicar reglas a nivel de subred o NIC

### 3. Conectividad Híbrida
Opciones para conectar tu VNet con redes locales:

- **[VPN Gateway](../../otro/conceptos-tecnicos.md#vpn-red-privada-virtual)**: Conexión segura sobre internet
- **[ExpressRoute](../../otro/conceptos-tecnicos.md#expressroute)**: Conexión dedicada con mayor ancho de banda y menor latencia
- **[Site-to-Site VPN](../../otro/conceptos-tecnicos.md#vpn-red-privada-virtual)**: Múltiples ubicaciones locales
- **[Point-to-Site VPN](../../otro/conceptos-tecnicos.md#vpn-red-privada-virtual)**: Usuarios remotos individuales

### 4. [Peering de VNets](../../otro/conceptos-tecnicos.md#peering-de-vnet)
Conecta dos VNets entre sí:
- **[VNet Peering](../../otro/conceptos-tecnicos.md#peering-de-vnet)**: Entre VNets en la misma región (bajo latencia, sin costo adicional)
- **Global VNet Peering**: Entre VNets en diferentes regiones

### 5. [Enrutamiento](../../otro/conceptos-tecnicos.md#enrutamiento) Personalizado
Define tablas de rutas personalizadas para controlar el flujo de tráfico:
- Rutas a aplicaciones virtuales de red (NVAs)
- Rutas a puertas de enlace VPN
- Rutas a ExpressRoute

### 6. [DNS](../../otro/conceptos-tecnicos.md#dns-sistema-de-nombres-de-dominio)
Cada VNet tiene:
- [DNS](../../otro/conceptos-tecnicos.md#dns-sistema-de-nombres-de-dominio) integrado de Azure
- Opción de usar servidores DNS personalizados
- Resolución de nombres para recursos dentro de la VNet

## Casos de Uso Comunes

### 1. Aplicaciones Web en Capas
```
VNet (10.0.0.0/16)
├── Frontend Subred (10.0.1.0/24) → Web Servers públicos
├── Backend Subred (10.0.2.0/24) → App Servers privados
└── Database Subred (10.0.3.0/24) → Databases privadas
```

### 2. Entornos Multientorno
```
VNet Producción → Subredes por componente
VNet Staging → Copia del entorno de producción
VNet Desarrollo → Para experimentación
```

### 3. Conectividad Híbrida
```
Centro de Datos Local ←(VPN/ExpressRoute)→ VNet Azure
```

### 4. Recuperación Ante Desastres
```
VNet Región Primaria
        ↓ (Replicación)
VNet Región Secundaria
```

## Ejemplo Práctico: Crear una VNet Completa

### Usando Azure Portal

1. **Crear la VNet**
   - Recurso → Virtual Network
   - Nombre: `vnet-produccion`
   - Espacio de direcciones: `10.0.0.0/16`
   - Suscripción y grupo de recursos

2. **Crear Subredes**
   - Frontend: `10.0.1.0/24`
   - Backend: `10.0.2.0/24`
   - Database: `10.0.3.0/24`

3. **Crear NSG para Frontend**
   - Permitir HTTP (80): Desde Internet
   - Permitir HTTPS (443): Desde Internet
   - Permitir SSH (22): Desde tu IP

4. **Crear NSG para Backend**
   - Permitir tráfico desde Frontend en puerto 8080
   - Denegar desde Internet

5. **Crear NSG para Database**
   - Permitir puerto 3306 solo desde Backend
   - Denegar todo lo demás

### Usando Azure CLI

```bash
# Crear grupo de recursos
az group create --name myResourceGroup --location eastus

# Crear VNet
az network vnet create \
  --resource-group myResourceGroup \
  --name vnet-produccion \
  --address-prefix 10.0.0.0/16

# Crear subred Frontend
az network vnet subnet create \
  --resource-group myResourceGroup \
  --vnet-name vnet-produccion \
  --name subnet-frontend \
  --address-prefixes 10.0.1.0/24

# Crear subred Backend
az network vnet subnet create \
  --resource-group myResourceGroup \
  --vnet-name vnet-produccion \
  --name subnet-backend \
  --address-prefixes 10.0.2.0/24

# Crear NSG para Frontend
az network nsg create \
  --resource-group myResourceGroup \
  --name nsg-frontend

# Crear regla para permitir HTTP
az network nsg rule create \
  --resource-group myResourceGroup \
  --nsg-name nsg-frontend \
  --name allow-http \
  --priority 100 \
  --direction Inbound \
  --access Allow \
  --protocol Tcp \
  --destination-port-ranges 80

# Asociar NSG a subred
az network vnet subnet update \
  --resource-group myResourceGroup \
  --vnet-name vnet-produccion \
  --name subnet-frontend \
  --network-security-group nsg-frontend
```

### Usando PowerShell

```powershell
# Variables
$resourceGroupName = "myResourceGroup"
$location = "eastus"
$vnetName = "vnet-produccion"
$vnetAddressSpace = "10.0.0.0/16"

# Crear grupo de recursos
New-AzResourceGroup -Name $resourceGroupName -Location $location

# Crear configuración de VNet
$subnetConfig = New-AzVirtualNetworkSubnetConfig `
  -Name "subnet-frontend" `
  -AddressPrefix "10.0.1.0/24"

# Crear VNet
$vnet = New-AzVirtualNetwork `
  -ResourceGroupName $resourceGroupName `
  -Name $vnetName `
  -AddressPrefix $vnetAddressSpace `
  -Subnet $subnetConfig `
  -Location $location

# Crear NSG
$nsg = New-AzNetworkSecurityGroup `
  -Name "nsg-frontend" `
  -ResourceGroupName $resourceGroupName `
  -Location $location

# Agregar regla
$nsgRule = New-AzNetworkSecurityRuleConfig `
  -Name "allow-http" `
  -Priority 100 `
  -Direction Inbound `
  -Access Allow `
  -Protocol Tcp `
  -SourcePortRange * `
  -DestinationPortRange 80 `
  -SourceAddressPrefix "*" `
  -DestinationAddressPrefix "*"

$nsg | Add-AzNetworkSecurityRuleConfig -Name "allow-http" -Direction Inbound `
  -Priority 100 -Access Allow -Protocol Tcp -SourceAddressPrefix "*" `
  -SourcePortRange "*" -DestinationAddressPrefix "*" -DestinationPortRange 80
```

## Mejores Prácticas

### 1. Planificación del Espacio de Direcciones
- ✅ Planifica con anticipación, elige rangos IP expandibles
- ✅ Usa subredes separadas para diferentes funciones
- ✅ Reserva espacio para futuros peerings de VNet
- ❌ No uses espacios de direcciones muy pequeños

### 2. Seguridad
- ✅ Implementa NSGs en todas las subredes
- ✅ Usa el principio de "least privilege" (menor privilegio)
- ✅ Revisa regularmente las reglas de NSG
- ✅ Considera Azure Firewall para protección adicional
- ❌ No permitas todo el tráfico de forma predeterminada

### 3. Monitoreo y Logging
- ✅ Habilita NSG Flow Logs
- ✅ Usa Azure Network Watcher para diagnósticos
- ✅ Monitorea la actividad de la red
- ✅ Configura alertas para cambios en la red

### 4. Optimización de Costos
- ✅ Usa VNet Peering en lugar de VPN cuando sea posible
- ✅ Consolida NSGs compartidos
- ✅ Elimina recursos no utilizados
- ✅ Usa Application Gateway para balanceo de carga eficiente

### 5. Escalabilidad
- ✅ Divide tu VNet en subredes pequeñas (delegación más granular)
- ✅ Usa múltiples NSGs si es necesario
- ✅ Considera VNet Peering para conectar múltiples VNets
- ✅ Planifica la capacidad de direcciones IP

## Integración con Otros Servicios Azure

### Compute
- [Virtual Machines (VMs)](../../otro/conceptos-tecnicos.md#virtual-machine-vm)
- App Service (con inyección de VNet)
- Container Instances
- [Kubernetes Service (AKS)](../../otro/conceptos-tecnicos.md#kubernetes)

### Bases de Datos
- [Azure SQL Database](../../otro/conceptos-tecnicos.md#database-base-de-datos)
- [Azure Database for MySQL/PostgreSQL](../../otro/conceptos-tecnicos.md#database-base-de-datos)
- [Cosmos DB](../../otro/conceptos-tecnicos.md#database-base-de-datos)
- Redis Cache

### Almacenamiento
- [Blob Storage](../../otro/conceptos-tecnicos.md#blob-storage) (con [Service Endpoints](../../otro/conceptos-tecnicos.md#service-endpoint))
- File Shares
- Data Lake Storage

### Seguridad
- Application Gateway
- [Azure Firewall](../../otro/conceptos-tecnicos.md#firewall)
- DDoS Protection
- Azure Bastion

## Limitaciones y Consideraciones

- **Número máximo de subredes por VNet**: 3,000
- **Número máximo de NICs por subred**: Sin límite (pero limitado por máquinas virtuales)
- **Número máximo de VNets por suscripción**: 1,000 (puede aumentarse solicitando)
- **No se pueden cambiar los rangos de direcciones**: Debes eliminar y recrear
- **Latencia**: El peering global puede tener mayor latencia que el regional

## Monitoreo y Diagnósticos

Azure proporciona varias herramientas:

1. **Network Watcher (Supervisión de Redes)**
   - Diagnóstico de conectividad
   - Captura de paquetes
   - Análisis de flujo NSG
   - Topología de red

2. **Monitor de Azure**
   - Métricas de red
   - Alertas
   - Log Analytics

3. **Application Insights**
   - Rendimiento de aplicaciones
   - Traces distribuidas

## Conclusión

Azure Virtual Network es el fundamento de cualquier infraestructura en Azure. Proporciona aislamiento, seguridad y control sobre tu red privada en la nube. Con una planificación cuidadosa del espacio de direcciones, implementación de seguridad robusta a través de NSGs y uso inteligente de subredes, puedes crear arquitecturas escalables, seguras y eficientes.

Una VNet bien diseñada facilita la integración de múltiples servicios Azure, proporciona conectividad segura con redes locales y permite el crecimiento futuro de tu infraestructura.

---

**Para más información:**
- [Documentación Oficial de Azure VNet](https://learn.microsoft.com/es-es/azure/virtual-network/virtual-networks-overview)
- [Mejores prácticas de networking en Azure](https://learn.microsoft.com/es-es/azure/cloud-adoption-framework/ready/azure-best-practices/network-segmentation-with-nvas)
- [Azure Network Watcher](https://learn.microsoft.com/es-es/azure/network-watcher/network-watcher-overview)

## Referencias

- [Azure Virtual Network Documentation](https://learn.microsoft.com/azure/virtual-network/)
- [NSG Security Rules](https://learn.microsoft.com/azure/virtual-network/network-security-groups-overview)
- [VNet Peering](https://learn.microsoft.com/azure/virtual-network/virtual-network-peering-overview)
- [Azure CLI - Virtual Network Commands](https://learn.microsoft.com/cli/azure/network/vnet)
- [Azure PowerShell - Network Cmdlets](https://learn.microsoft.com/powershell/module/az.network/)

## Tags

- #Azure
- #VNet
- #Networking
- #Cloud
- #Seguridad
- #Infrastructure
