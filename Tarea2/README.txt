## Requisitos

- Docker y Docker Compose
- tcpdump
- Wireshark

## Levantar el servicio

```bash
git clone https://github.com/vicenteibarra1-coder/tarea2-rtsp.git
cd tarea2-rtsp
docker compose up -d
docker ps
docker compose down
```

## Captura con RTSP sobre UDP

Terminal 2 (crear la red sin encender los contenedores):

```bash
docker compose down
docker compose up --no-start
```

Terminal 1 (empezar a grabar):

```bash
sudo tcpdump -i br-rtsp -w captura_udp.pcap
```

Terminal 2 (encender, esperar y apagar):

```bash
docker compose up -d
sleep 30
docker compose stop
```

Terminal 1: `Ctrl + C` para detener la grabación.

Terminal 2:

```bash
docker compose down
```

## Captura con RTSP sobre TCP

Mismos pasos, cambiando el nombre del archivo y el comando de inicio:

```bash
docker compose down
docker compose up --no-start
```

```bash
sudo tcpdump -i br-rtsp -w captura_tcp.pcap
```

```bash
docker compose -f docker-compose.yml -f docker-compose.tcp.yml up -d
sleep 30
docker compose stop
```

`Ctrl + C` en la terminal 1, y después:

```bash
docker compose down
```

## Análisis en Wireshark

Abrir el archivo `.pcap` (Archivo → Abrir) y usar estos filtros:

| Filtro | Qué muestra |
|---|---|
| `rtsp` | Mensajes de control: OPTIONS, ANNOUNCE, DESCRIBE, SETUP, RECORD, PLAY, GET_PARAMETER, TEARDOWN |
| `rtp` | Paquetes de video (PT 96, H.264) y audio (PT 97, AAC) |

link_video_Demostracion(solo con cuenta UDP): (https://drive.google.com/file/d/1ic0UA1sblKpRajPfotg30tdmKNgkwxKQ/view)
link_video_Demostracion(enlace publico): (link_video_Demostracion(solo con cuenta UDP): (https://drive.google.com/file/d/1ic0UA1sblKpRajPfotg30tdmKNgkwxKQ/view))
