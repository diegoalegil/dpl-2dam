# Mis máquinas en la nube: producción y staging

Empiezo el 23/10/2026, después de la clase del apunte 08. Necesito mis propias dos máquinas en la nube, como el profe: una de **producción** y otra de **staging**.

## Qué necesito

- Dos máquinas virtuales con **Linux Ubuntu LTS**.
- Cada una con **IPv4 pública**, para llegar a ella desde internet.
- Acceso por **SSH** con clave, una clave distinta por máquina.
- Que sea gratis o casi, y que **no me puedan cobrar por sorpresa**.
- Que aguante todo el curso, también el **proyecto final en Java**, que pide bastante RAM.
- Mejor si son **ARM**, como mi Mac (ver más abajo por qué).

## Vocabulario nuevo

| Término | Qué es |
|---|---|
| Capa gratuita (*free tier*) | Lo que un proveedor de nube te deja usar sin pagar |
| Siempre gratis (*Always Free*) | Gratis sin fecha de fin, mientras respetes los límites |
| Créditos | Saldo de regalo, en dólares, que se gasta al usar máquinas. Caduca |
| Pago por uso (*Pay As You Go*) | Cuenta en la que pagas lo que gastes por encima de lo gratis |
| vCPU | Una CPU virtual. Suele ser medio núcleo o un núcleo compartido |
| Retención en la tarjeta | Te bloquean una cantidad pequeña para comprobar que la tarjeta es real y luego la devuelven. No es un cobro |
| Región | La ciudad o zona donde están físicamente las máquinas (Madrid, Frankfurt...) |
| Región de origen (*home region*) | En Oracle, la región que eliges al crear la cuenta. Lo gratis solo vale ahí y **no se puede cambiar después** |
| VPS | Servidor privado virtual. Una máquina virtual que alquilas por un precio fijo al mes |

## Comparativa (datos de octubre de 2026)

Las ofertas cambian mucho. Estos datos los comprobé el 23/10/2026.

| Opción | Coste real | Tarjeta | Duración | Máquinas (CPU y RAM) | Arquitectura | IPv4 pública | Riesgo de cobro | Java final | Facilidad |
|---|---|---|---|---|---|---|---|---|---|
| **Oracle Always Free** | 0 € | Sí (débito o crédito) | Siempre | 2 de 1 OCPU y 6 GB. Además, 2 AMD de 1 GB | ARM (las A1) | Incluida | Nulo si no paso a pago por uso | Sí | Media. Es la consola del profe |
| **AWS (plan gratuito)** | 0 € durante 6 meses | Normalmente no | Máximo 6 meses o hasta gastar los créditos (100 $ + hasta 100 $) | t4g.small: 2 vCPU y 2 GB. Solo una es gratis hasta el 31/12/2026, la otra gasta créditos | ARM o x86 | Se cobra (unos 3,6 $ al mes cada una) del crédito | Nulo en el plan gratuito, pero luego la cuenta se suspende | Justo | Media o difícil |
| **Google Cloud** | 1 máquina gratis. La segunda, de pago | Sí | Siempre (1 e2-micro) + 300 $ durante 90 días | e2-micro: 2 vCPU compartidas y 1 GB | x86 | Probablemente se cobra (unos 3,6 $ al mes) | Bajo, pero hay que vigilar | No | Media |
| **Azure for Students** | 0 €. Las IP salen del crédito | No | 12 meses (100 $), renovable mientras sea estudiante | B1s (1 vCPU), B2pts v2 o B2ats v2 (2 vCPU). Todas con 1 GB | ARM o x86 | Se cobra (unos 3,6 $ al mes cada una) del crédito | Nulo: al acabar el crédito se desactiva | No (1 GB) | Media |
| **GitHub Student Pack** | No da máquinas propias | No | | DigitalOcean salió del pack en julio de 2026. Lo que queda de nube es Azure for Students | | | | | |
| **Hetzner** | Unos 6 € al mes por máquina | Sí | Mientras pague | CAX11: 2 vCPU ARM y 4 GB | ARM o x86 | Incluida | Bajo (precio fijo) | Sí | Fácil, pero ahora no deja contratar |
| **VPS barato (OVHcloud, netcup...)** | Unos 4 a 7 € al mes por máquina | Sí | Mientras pague | 2 vCPU y 4 GB o más | x86 | Incluida | Bajo (precio fijo) | Sí | Fácil |

### Notas de cada opción

- **Oracle**: la más generosa gratis con diferencia. Problemas conocidos:
  - A veces sale **"Out of host capacity"**: no quedan máquinas ARM gratis libres en esa región. Hay que reintentar más tarde.
  - Oracle puede **recuperar máquinas ociosas**: si durante 7 días la CPU, la red y la memoria están por debajo del 20 %, puede quitártela.
  - Ya **recortó la oferta una vez** sin avisar mucho (ver abajo).
  - No acepta tarjetas prepago ni virtuales.
- **AWS**: desde julio de 2025 las cuentas nuevas ya no tienen 12 meses gratis. Tienen un plan gratuito de 6 meses con créditos. Si no paso a la cuenta de pago, a los 6 meses suspenden la cuenta y borran todo a los 90 días. No llega al final del curso.
- **Google Cloud**: solo una máquina gratis y solo en regiones de Estados Unidos. Para dos máquinas no sirve.
- **Azure for Students**: es la única opción seria **sin tarjeta**. Pero es para estudiantes con correo del centro y puede que no acepte todos los correos de FP. Con 1 GB de RAM no da para Java. Para más RAM hay que pagar con el crédito y se acaba en 2 o 3 meses.
- **GitHub Student Developer Pack**: lo de DigitalOcean (200 $) se acabó el 31/07/2026. Heroku no da una máquina con SSH, es otra forma de desplegar.
- **Hetzner**: era la más recomendada de pago, pero en 2026 subió precios dos veces y desde junio **no deja crear servidores a clientes nuevos**. En octubre de 2026 sus planes baratos salen como "no disponible".
- **VPS de pago**: lo más fiable y sencillo, pero cuesta dinero todos los meses. Es el plan B si Oracle falla.

### ¿Y un VPS de 1 € al mes?

Lo miré el 23/10/2026. Los VPS de 1 € al mes que salían en reseñas antiguas (IONOS XS, Strato VC 1-1) **ya no existen**. Lo más barato que hay:

| Opción | Precio real | Máquina | Pegas |
|---|---|---|---|
| Ofertas anuales tipo RackNerd | Unos 11 $ al año por máquina (menos de 1 $ al mes) | 1 vCPU y 1 GB, x86 | Solo salen en épocas de ofertas (Black Friday, Año Nuevo). Se paga el año por adelantado. 1 GB no da para Java. Empresa pequeña de EE. UU. |
| Strato VPS S | 2 € al mes en la oferta, luego 4 € al mes con IVA, más 9 € de alta | 1 vCPU y 2 GB, x86 | Web en alemán. Para Java va justo |
| IONOS VPS S+ | 2 € + IVA los 3 primeros meses, luego unos 5 € + IVA, más 10 € + IVA de alta | 1 vCPU y 2 GB, x86 | Para Java va justo |

Conclusión: por menos de 1 € al mes hay máquinas de 1 GB, pero no cumplen lo del proyecto en Java. Todas piden tarjeta o PayPal igual que Oracle. Oracle da 6 GB por 0 €.

## Cambio importante en Oracle (junio de 2026)

Oracle **ha recortado a la mitad** la parte ARM gratis:

| | Antes | Desde junio de 2026 |
|---|---|---|
| Horas de OCPU al mes | 3.000 | 1.500 |
| Horas de GB al mes | 18.000 | 9.000 |
| Equivale a | 4 OCPU y 24 GB | **2 OCPU y 12 GB** |

Lo aplicó a la fuerza el 18/08/2026: las máquinas que pasaban del límite se borraron.

Para mí significa que **no puedo** tener dos máquinas de 2 OCPU y 12 GB como explicó el profe. Lo que cabe gratis son **dos máquinas de 1 OCPU y 6 GB** cada una. Para el curso y para Java sobra.

Las 2 máquinas AMD pequeñas (1/8 de OCPU que puede usar más a ratos y 1 GB) siguen igual.

## Por qué prefiero ARM

Mi Mac es ARM (Apple Silicon). Kamal construye la imagen Docker en mi Mac:

- Si el servidor es **ARM**, la imagen se construye para mi misma arquitectura (`arm64`). Es rápido y sin trucos.
- Si el servidor es **AMD o Intel**, hay que construirla para `amd64` y el Mac tiene que emularlo. Va más lento y a veces falla.

En `config/deploy.yml` de Kamal se indica así:

```yaml
builder:
  arch: arm64   # el profe, con su máquina AMD, pone amd64
```

## Qué elijo y por qué

Elijo **Oracle Cloud Always Free**, con dos máquinas ARM (Ampere A1) de 1 OCPU y 6 GB: `produccion` y `staging`.

- Es la única opción gratis que no caduca y que da RAM de sobra para Java.
- Es ARM, como mi Mac, así que Kamal construye la imagen sin emular.
- Es la misma consola que usa el profe en clase.
- Tengo tarjeta para la verificación. Mientras no pase a pago por uso, no me pueden cobrar.

Plan B si Oracle no me deja crear las máquinas: un VPS de pago de 2 GB (Strato o IONOS).

## Cuántas máquinas gratis da Oracle

Con una cuenta Always Free puedo tener **hasta 4 máquinas a la vez**:

| Tipo | Cuántas | CPU y RAM | Arquitectura |
|---|---|---|---|
| Ampere A1 (`VM.Standard.A1.Flex`) | 1 o 2 | 2 OCPU y 12 GB en total, a repartir. Con dos, 1 OCPU y 6 GB cada una | ARM |
| AMD Micro (`VM.Standard.E2.1.Micro`) | 2 | 1/8 de OCPU (puede usar más a ratos) y 1 GB cada una | x86 |

Límites que hay que vigilar:

- **Disco**: 200 GB en total entre todas. Cada máquina gasta unos 50 GB de disco de arranque, así que 4 máquinas son justo 200 GB. Si hago un disco más grande, la cuarta ya no cabe gratis.
- **Una sola cuenta gratis por persona.** Crear varias va contra las normas y te pueden cerrar todas.
- Lo gratis solo vale en mi **región de origen**.

Mi reparto: las dos A1 para `produccion` y `staging`. Las dos AMD las dejo libres por ahora.

## Fuentes

- Oracle, recursos Always Free: https://docs.oracle.com/en-us/iaas/Content/FreeTier/freetier_topic-Always_Free_Resources.htm
- Recorte de Oracle: https://linuxiac.com/oracle-quietly-cuts-free-tier-ampere-a1-resources-in-half/
- AWS, plan gratuito: https://aws.amazon.com/free/free-tier-faqs/
- AWS, prueba de t4g.small: https://aws.amazon.com/ec2/instance-types/t4/
- Google Cloud, capa gratuita: https://docs.cloud.google.com/free/docs/free-cloud-features
- Azure for Students: https://azure.microsoft.com/en-us/free/students
- DigitalOcean sale del GitHub Student Pack: https://github.com/orgs/community/discussions/200663
- Hetzner sin disponibilidad: https://stackvaluelab.com/hetzner-cx-cax-unavailable/
- Strato, VPS Linux: https://www.strato.de/server/linux-vserver/
- IONOS España, VPS: https://www.ionos.es/servidores/vps
- RackNerd, VPS KVM: https://www.racknerd.com/kvm-vps
