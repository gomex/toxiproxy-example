# toxiproxy-example

## Objetivo

Uma forma mais simples de executar o [toxiproxy](https://github.com/Shopify/toxiproxy)

## Como usar

### Configure seu toxiproxy

Crie um arquivo chamado **config/toxiproxy.json**. Você pode usar o exemplo **config/toxiproxy.json.example**:

```bash
cp config/toxiproxy.json.example config/toxiproxy.json
```

Modifique o arquivo para colocar quantas conexões desejar, mas lembre-se de modificar o **docker-compose** no service **toxiproxy** para a porta desejada.

```json
{
      "name": "web_dev_frontend_1",
      "listen": "[::]:18080",
      "upstream": "webapp:8080",
      "enabled": true
    }
```

No exemplo acima, a porta que o container precisa publicar é **18080**, pois a porta do **upstream** é uma comunicação entre containers na mesma reda interna do Docker. Se os dois containers estiverem dentro do docker-compose na mesma rede você não terá problemas. 

Obs: Se nenhuma rede é informada no docker-compose eles por padrão fazem parte da mesma rede.

### Iniciando seu toxiproxy

```
docker-compose up
```