# 🤖 TERMINATOR Framework


***Web Procesamiento y Entrenamiento: [WAI.CAM](http://wai.cam)***


**Framework de Inferencia Dirigida Multimodal**

Sistema completo para inferencia con modelos de IA, procesamiento de audio/voz, detección de idioma, generación de animaciones 3D, y API REST lista para producción.

## 🚀 Inicio Rápido

```bash
# 1. Extraer framework
unzip TERMINATOR_Complete.zip
cd TERMINATOR

# 2. Ejecutar script de inicio
./scripts/start.sh
```

El servidor arrancará en `http://localhost:8000`

## 📋 Características

✅ **Inferencia Dirigida (Steerable )** - Control preciso de la generación mediante vectores de steering✅ **Multi-GPU** - Soporte para 1-4+ GPUs con paralelización automática✅ **Detección de Idioma** - Identificación automática de español, inglés, francés, alemán, italiano, portugués✅ **Procesamiento de Audio** - Transcripción con Whisper, síntesis con ElevenLabs✅ **Animación 3D** - Generación de modelos animados sincronizados con audio✅ **API REST** - FastAPI con documentación interactiva✅ **NVMe Storage** - Gestión de pesos en discos NVMe separados✅ **Servidor Local** - Integración con XAMPP/Apache

## 📖 Documentación

- **Manual Completo**: Ver archivo `TERMINATOR`

- **API Docs**: [http://localhost:8000/docs](http://localhost:8000/docs)

- **ReDoc**: [http://localhost:8000/redoc](http://localhost:8000/redoc)

## 🖥️ Requisitos

### Mínimos

- Python 3.10+

- 32 GB RAM

- 1x GPU NVIDIA (16 GB VRAM )

- 500 GB SSD

### Recomendados

- Python 3.10+

- 64-128 GB RAM

- 2-4x GPU NVIDIA RTX 4090 / A100

- 2-4x NVMe 2TB

## 📦 Instalación Manual

```bash
# Crear entorno virtual
python3 -m venv venv
source venv/bin/activate

# Instalar dependencias
pip install -r requirements.txt

# Iniciar servidor
python -m uvicorn api.main:app --host 0.0.0.0 --port 8000
```

## 🔌 Uso de la API

### Inferencia

```bash
curl -X POST http://localhost:8000/api/v1/inference \
  -H "Content-Type: application/json" \
  -d '{"prompt": "Explica la teoría de la relatividad", "max_length": 200}'
```

### Síntesis de Audio

```bash
curl -X POST http://localhost:8000/api/v1/audio/synthesize \
  -H "Content-Type: application/json" \
  -d '{"text": "Hola mundo", "voice_id": "default"}' \
  --output audio.mp3
```

### Detección de Idioma

```bash
curl -X POST http://localhost:8000/api/v1/language/detect \
  -H "Content-Type: application/json" \
  -d '{"text": "Hola, ¿cómo estás?"}'
```

## 🎮 Configuración Multi-GPU

Editar `config/config.yaml`:

```yaml
gpu:
  enabled: true
  devices: [0, 1, 2, 3]  # IDs de GPUs
  strategy: "data_parallel"  # data_parallel, model_parallel, pipeline
  memory_fraction: 0.9
```

## 💾 Configuración NVMe

```yaml
storage:
  nvme_paths:
    - "/mnt/nvme0/models"
    - "/mnt/nvme1/models"
    - "/mnt/nvme2/cache"
  model_sharding: true
  cache_size_gb: 50
```

## 🌐 Servidor con XAMPP

Ver sección "Servidor con XAMPP" en el archivo `TERMINATOR` para configuración completa.

## 🚀 Despliegue en Producción

### Systemd Service

```bash
sudo cp scripts/terminator.service /etc/systemd/system/
sudo systemctl enable terminator
sudo systemctl start terminator
```

### Docker

```bash
docker build -t terminator:latest .
docker run -d --name terminator --gpus all -p 8000:8000 terminator:latest
```

## 📊 Monitoreo

```bash
# Ver logs
tail -f logs/terminator.log

# Monitorear GPUs
watch -n 1 nvidia-smi

# Estado del servicio
sudo systemctl status terminator
```

## 🔧 Solución de Problemas

Ver sección "Solución de Problemas" en el archivo `TERMINATOR`.

## 📁 Estructura del Proyecto

```
TERMINATOR/
├── api/              # API REST con FastAPI
├── audio/            # Procesamiento de audio
├── core/             # Detección de idioma
├── inference/        # Motor de inferencia dirigida
├── vision/           # Animación 3D
├── utils/            # Gestión GPU y NVMe
├── config/           # Configuración YAML
├── scripts/          # Scripts de utilidad
├── TERMINATOR        # Manual completo
├── requirements.txt  # Dependencias
└── README.md         # Este archivo
```

## 📄 Licencia

MIT License

## 📞 Soporte

- **Documentación**: `/docs` en el servidor

- **Manual**: Ver archivo `TERMINATOR`

---

**TERMINATOR Framework v1.0.0***Listo para Producción*

