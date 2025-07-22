# Use uma imagem oficial do Python como imagem base. A versão alpine é leve.
FROM python:3.13.4-alpine3.22

# Define o diretório de trabalho dentro do contêiner
WORKDIR /app

# Copia o arquivo de dependências para o diretório de trabalho
COPY requirements.txt .

# Instala as dependências especificadas no requirements.txt
# --no-cache-dir: Desativa o cache, o que é útil para manter o tamanho da imagem menor.
# --upgrade pip: Garante que temos a versão mais recente do pip.
RUN pip install --no-cache-dir --upgrade pip -r requirements.txt

# Copia o restante do código da aplicação para o diretório de trabalho
COPY . .

# Expõe a porta em que o app será executado
EXPOSE 8000

# Define o comando para executar a aplicação quando o contêiner iniciar
# Usamos 0.0.0.0 para tornar a aplicação acessível de fora do contêiner.
CMD ["uvicorn", "app:app", "--host", "0.0.0.0", "--port", "8000", "--reload"]
