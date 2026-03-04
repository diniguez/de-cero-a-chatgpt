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
