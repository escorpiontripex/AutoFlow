# AutoFlow

**Alumno:** Adrián Rodado · **Ciclo:** ASIR (2º) · **Módulo:** Proyecto Intermodular

## Descripción
AutoFlow es una plataforma que automatiza el despliegue y la configuración de la infraestructura de una empresa cliente. A partir de una plantilla, crea las máquinas y las redes (Terraform) y las configura (Ansible) sin pasos manuales, de forma repetible y versionada.

## Objetivo de la infraestructura
Montar de forma automática una red de empresa segmentada en VLAN (gestión, DMZ, internos y datos) con servidor web, base de datos, DNS, cortafuegos, monitorización y copias de seguridad, accesible solo mediante VPN y bastión.

## Tecnologías utilizadas
| Categoría | Tecnología |
|---|---|
| Virtualización | Proxmox VE (KVM + LXC) |
| Sistemas operativos | Ubuntu Server 24.04, Debian 13, Rocky Linux 9 |
| Servidor web | Nginx (proxy inverso) y Apache |
| Base de datos | PostgreSQL |
| Contenedores | LXC y Docker |
| Automatización | Terraform, Ansible, Bash |
| Firewall | pfSense y nftables |
| Monitorización | Prometheus y Grafana |
| Copias de seguridad | Bash (tar, rsync, pg_dump) y vzdump |
| Control de versiones | Git y GitHub |

## Estructura del repositorio
```
AutoFlow/
├── playbooks/        # site.yml: playbook principal
├── roles/            # seguridad, firewall, dns, servicios_web,
│                     # base_datos, monitorizacion, backups
├── variables/        # variables por entorno (secretos cifrados con Ansible Vault)
├── plantillas/       # plantillas Jinja2 y de máquinas
├── inventario/       # hosts.ini con los grupos de servidores
├── terraform/        # código de creación de máquinas y redes
├── scripts/          # desplegar.sh y copias de seguridad
├── tests/            # comprobaciones tras el despliegue
├── documentacion/    # memoria y diagramas
├── ansible.cfg
└── README.md
```

## Uso básico
```bash
ansible-playbook playbooks/site.yml --syntax-check
ansible-playbook playbooks/site.yml
```
