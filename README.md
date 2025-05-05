# n8n Docker Setup

Este repositório contém a configuração para rodar o n8n localmente usando Docker.

## Configuração

1. Clone este repositório:
   ```bash
   git clone <URL_DO_REPOSITORIO>
   ```

2. Crie um arquivo `.env` baseado no modelo `.env.example`:
   ```bash
   cp .env.example .env
   ```
   Atualize as variáveis no arquivo `.env` com suas credenciais.

3. Suba o serviço com Docker Compose:
   ```bash
   docker-compose up -d
   ```

4. Acesse o n8n em [http://localhost:5678](http://localhost:5678).

## Aviso Importante

Ao utilizar o n8n com volumes mapeados, é possível que ocorram problemas de permissão ao acessar os arquivos no diretório `n8n_data`. Certifique-se de ajustar as permissões do diretório para o usuário correto (por exemplo, `1000:1000`) para evitar erros de acesso.

### Exemplo de Ajuste de Permissões

Se você encontrar problemas de permissão ao iniciar o n8n, execute o seguinte comando para corrigir as permissões do diretório `n8n_data`:

```bash
sudo chown -R 1000:1000 /caminho/para/n8n_data
```

Substitua `/caminho/para/n8n_data` pelo caminho real do diretório no seu sistema. Após ajustar as permissões, reinicie o serviço com:

```bash
docker-compose down && docker-compose up -d
```

## Estrutura do Repositório

- `docker-compose.yml`: Configuração do Docker Compose para o n8n.
- `.env.example`: Modelo para as variáveis de ambiente.
- `.gitignore`: Arquivo para ignorar arquivos sensíveis e desnecessários no repositório.
- `n8n_data/`: Diretório para persistência de dados do n8n (ignorado pelo Git).

## Notas

Certifique-se de usar uma senha segura no arquivo `.env` para proteger o acesso ao n8n.