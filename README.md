# google-assistant-rpi

Passos para configurar o Google Assistant em um Raspberry Pi 3

- Baixar o arquivo `.asoundrc` com a configuração do microfone e speaker.
- Instalar dependências:
  - `sudo apt-get install python3-dev python3-venv`
  - `python3 -m venv env`
  - `env/bin/python -m pip install --upgrade pip setuptools wheel`
  - `source env/bin/activate`
  - `sudo apt-get install portaudio19-dev libffi-dev libssl-dev libmpg123-dev`
  - `python -m pip install --upgrade google-assistant-library==1.1.0`
  - `python -m pip install --upgrade 'google-assistant-sdk[samples]'`
  - `python -m pip install --upgrade 'google-auth-oauthlib[tool]'`
- Criar um projeto na Cloud do Google:
  - Configurar credenciais [aqui](https://developers.google.com/assistant/sdk/guides/library/python/embed/config-dev-project-and-account).
- Autenticar o Raspberry Pi:
  ```
  google-oauthlib-tool --scope https://www.googleapis.com/auth/assistant-sdk-prototype \
	--scope https://www.googleapis.com/auth/gcm \
	--save --headless --client-secrets /caminho/para/client_secret_client-id.json
  ```
- Tela de permissão de OAuth em: https://console.cloud.google.com/apis/dashboard
  - Adicionar usuários
  - Definir como uso externo
  - Publicar
- Inicie o Google Assistant
  - `google-assistant-demo --device-model-id rpi-ga-rpi-xsjay  --project-id rpi-ga-dsdax`
  - Irá aparecer uma mensagem de erro e um link parar ativar a API
