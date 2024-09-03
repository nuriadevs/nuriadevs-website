---
title: "Whisper de OpenAI y Pytube"
date: 2024-08-31
draft: false
description: "Explorando Whisper de OpenAI y Pytube"
tags: [OpenAI, Artificial Intelligence, Pytube, YouTube, Python, Transcription , Script]
---



## Explorando Whisper de OpenAI y Pytube para la Transcripción de Audio y Descarga de Videos

![mano robot y mano humana](https://images.unsplash.com/photo-1680783954745-3249be59e527?q=80&w=1964&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D)


Photo by [Cash Macanaya](https://unsplash.com/es/@cashmacanaya) on [Unsplash](https://unsplash.com/es)

La transcripción de videos ofrece una serie de beneficios, como mejorar la accesibilidad para personas con discapacidades auditivas, facilitar la búsqueda de información, permitir la creación de subtítulos y traducciones automáticas, o para trabajar con cualquier contenido multimedia.

Por un lado, encontramos a **Whisper**, un modelo de inteligencia artificial de código abierto desarrollado por **OpenAI**. Este modelo no solo facilita la conversión precisa de voz a texto, sino que también cuenta con la capacidad para detectar cualquier idioma de manera eficiente. Por otro lado, la biblioteca de **Python PyTube** está diseñada para descargar videos desde la plataforma de **YouTube**.

Si queremos transcribir el audio de cualquier video de **Youtube**, podemos realizarlo llevando cada paso del siguiente script:

## Transcripción de Audio de un Video de YouTube

### Instalar las dependencias necesarias

Se instalan las bibliotecas necesarias para utilizar el modelo de transcripción de voz **Whisper**.
```
!pip install -U openai-whisper  
!pip install --upgrade whisper
```
### Instalación de bibliotecas para manipulación de videos y audio

Se instalan las bibliotecas **Pytube** y **ffmpeg-python** para la manipulación de videos y la descarga de audio.
```
!python -m pip install pytube  
!pip install ffmpeg-python
```
### Importar las bibliotecas necesarias
```
from pytube import YouTube  
import whisper
```
### Configurar el enlace de YouTube

El audio del video es el poema “Splendour in the grass” de William Wordsworth.
```
youtubeID = 'https://www.youtube.com/watch?v=-6JIaWigm-c'
```
### Cargar el modelo de transcripción

Carga del modelo para la transcripción de voz.
```
model = whisper.load_model('small')
```
### Subir el video desde YouTube

Se utiliza la biblioteca **Pytube** para subir el video desde **YouTube** y obtener información sobre él.
```
letterVideoYT = YouTube(youtubeID)
```
### Obtener el audio del video

Se extrae el audio del video utilizando la función **get_audio_only()** de **Pytube**, que obtiene la pista de audio del video.
```
audio = letterVideoYT.streams.get_audio_only()
```
### Descargar el archivo de audio

El audio del video se descarga y se guarda en un archivo llamado ‘audio.mp4’ en el directorio ‘/content/’.
```
audio.download(filename='/content/audio.mp4')
```
### Transcribir el audio utilizando el modelo

Se utiliza el modelo **Whisper** previamente cargado para transcribir el audio del archivo ‘audio.mp4’.
```
result = model.transcribe('audio.mp4')
```
### Guardar el resultado en un archivo de texto

El resultado de la transcripción se guarda en un archivo de texto llamado ‘resultado.txt’ en el formato UTF-8.
```
with open('resultado.txt', 'w', encoding='utf-8') as file:  
    file.write(result["text"])  
  
print("Resultado guardado en 'resultado.txt'")
```
Siguiendo los pasos anteriores, obtendrás la transcripción del video de **YouTube** en un archivo de texto. Aunque si deseas descargar el archivo, puedes hacerlo accediendo al enlace del repositorio.

{{< github repo="nuriadevs/youtube-audio-transcriber" >}}

Espero que el artículo haya sido de utilidad para ti. 🍀