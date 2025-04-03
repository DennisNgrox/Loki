# Laboratório Loki

Este repositório contém um projeto desenvolvido para realizar laboratórios. Além disso, utilizei o flog para gerar logs para testes.
Varios promtail-config serão adicionados, cada um tratando de uma funcionalidade do promtail.
<p></p>

 ![Open Source ❤️](https://img.shields.io/badge/Open%20Source-blue) ![Grafana](https://img.shields.io/badge/Grafana%20Loki-orange) ![Project-learning](https://img.shields.io/badge/Learning%20Project-green)

## Sumário

- [Instalação](#instalação)
- [Como Utilizar](#como-utilizar)
- [Configuração do Promtail](#configuração-do-promtail)
- [Gerar Logs com flog](#gerar-logs-com-flog)


## Instalação

Para clonar o repositório e instalar as dependências, siga os seguintes passos:

```bash
git clone https://github.com/DennisNgrox/Loki.git
cd Loki
````

<h3>Como Utilizar</h3>
<h1></h1>
Este projeto foi criado para realizar laboratórios utilizando Pipeline Stages para adicionar labels através de regex. Abaixo estão os passos para configurar e utilizar o projeto.

<h3>Configuração do Promtail</h3>
<h1></h1>
O arquivo de configuração do Promtail (promtail-config.yaml) deve ser ajustado conforme necessário. Você pode encontrar o arquivo de configuração em promtail-config.yaml.

Exemplo de configuração:
```yaml
server:
  http_listen_port: 9080
  grpc_listen_port: 0

positions:
  filename: /tmp/positions.yaml # Nesse arquivo o Promtail guarda a posição que o promtail parou na leitura dos arquivos de log.

clients:
  - url: http://192.168.15.6:3100/loki/api/v1/push # IP de envio dos logs para o backend Loki

scrape_configs: # Sessão de Scrape
  - job_name: docker-logs # Nome do Job
    docker_sd_configs: # Utilitário para realizar scrape do docker (Discovery)
      - host: unix:///var/run/docker.sock # Socket utilizado.
        refresh_interval: 5s # Discovery a cada 5 segundos
        filters: # Filtros
          - name: name
            values: [prometheus] # Realizará o scrape apenas do container com nome "prometheus"
    pipeline_stages: # Estagio de alterações, adições, analises dos logs.
      - docker: {} # Utilizado para tratativa do docker, gera valores em especifico como logs, stream (stdout ou stderror) e timestamp
    relabel_configs: # Alterando labels para o nome do container
      - source_labels: ['__meta_docker_container_name'] 
        regex: '/([^\.]+)'
        target_label: 'container_name'
        replacement: '$1'

```

<h3>Gerar Logs com flog</h3>
<h1></h1>
Utilizamos a ferramenta flog para gerar logs de teste. Para gerar logs utilizando flog, execute o seguinte comando:

```bash
docker run -it mingrammer/flog flog -s 10s -n 50 >> arquivo.log
```

Este comando irá gerar 50 logs a cada 10 segundos e salvar em um arquivo chamado arquivo.log.

<h1></h1>

```code

Certifique-se de ajustar o conteúdo do arquivo `promtail-config.yaml` conforme necessário e adicionar descrições mais detalhadas sobre como utilizar as funcionalidades específicas do projeto, se necessário.
```
