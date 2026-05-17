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
![image alt](https://github.com/Slucina04060708/copy-fail-challenge-1/blob/d2afcf40686e18b8b5d90dc40c724590b749f757/Screenshot%202026-05-16%20234435.png)
