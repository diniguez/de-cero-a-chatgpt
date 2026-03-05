días 2 y 3:
Ronghao Pan
ronghao.pan@um.es
Investiga doctorando 2º año LLMs, ASR, VLM

día 1 y 4:
José Antonio Herández López
joseantonio.hernandez6@um.es
Investiga dorctorando y profesor UMU
LLMs para generar código


Modelos Bert: para clasificación de sentimientos y emociones

FNN = Multi Layer Perceptron

causal_laguage_model es cuando hacemos MASK de la matriz triangular inferior con torch.triu

https://bbycroft.net/llm

Para elegir modelo:
1-Creador del modelo
2-monolingüe/multilingüe (tener en cuenta los dialectos, por ejemplo inglés hindú)
3-número de descargas
4-tipo de tarea (clasificación, ordenación, resumenes,...)


GGUF es una compresión del modelo para usar solamente CPU, para máquinas sin GPU

Los modelos base a los que se les aplica un instruct-tunning, llevan el sufijo -it, ejemplo:
gemma-7b-it https://huggingface.co/google/gemma-7b-it

Vision Transformer: por ejemplo clip-vit-base-patch32
https://huggingface.co/openai/clip-vit-base-patch32

# Longitud máxima de secuencia
max_length = 256
para averiguar la correcta, mirar en el modelo en huggingface, en el fichero config.json context_length por ejemplo

en caso de Out of memory error:
reducir estos hiperparámetros:
    per_device_train_batch_size=16,
    per_device_eval_batch_size=32,
y activar el hiperparámetro:
    fplg

# Modelos fundacionales y SFT(Supervised Fine-Tunned)
existen modelos fundacionales, se suelen etiquetar con el sufijo "-b" que para ser utilziados deben ser fine-tuneados o darles un prompt bien formateado (leer la documentación del modelo para ver si es el caso y cómo usarlo). Tampoco soportan chat, sólo funcionan en modo 1pregunta-1respuesta.

# Modelos Instruct
Los SFT son muy directos, dan solamente la respuesta pedida, sin introducción, explicación o preguntando para resolver ambigüedades.
usando libreria TRL de convertir de modelo fundacional a SFT

# Modelos con Reinforcement Learning, tipo ChatGPT
RLHF(Reinforcement Learning from Human Feedback) añade verbosidad para seguir instrucciones adaptadas a las preferencias de las conversaciones humanas, es ahora mismo el punto donde las empresas se diferencian unas de otras y recelosos de compartir los detalles de estos procesos.

# PEFT

Ahorro de costes y espacio para entrenar, 1ª solucion es dejar algunas capas sin entrenar, y entrenar las últimas capas

# LoRA

en el ejemplo de 5_decoder_sft_lora.ipynb
    per_device_train_batch_size=4, # batch size pequeño para que quepa en GPU
    gradient_accumulation_steps=8, # acumulamos gradientes para simular un batch size mayor
da lugar a un batch size efectivo de 4x8 = 32

# Cuantización = Reducción de la precisión a 8B, 4B integer
PTQ significa que usa un Grupo de calibración y da mejores resultados, casi tan preciso como el modelo no cuantizado.
