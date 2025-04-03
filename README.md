# Laboratório Loki

Este repositório contém um projeto desenvolvido para realizar laboratórios utilizando Pipeline Stages para adicionar labels através de regex. Além disso, utilizamos o flog para gerar logs para testes.
Varios promtail-config serão adicionados, cada um tratando de uma funcionalidade do promtail.

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
<conteúdo do arquivo promtail-config.yaml>
```

<h3>Gerar Logs com flog</h3>
<h1></h1>
Utilizamos a ferramenta flog para gerar logs de teste. Para gerar logs utilizando flog, execute o seguinte comando:

```bash
docker run -it mingrammer/flog flog -s 10s -n 50 >> arquivo.log
```

Este comando irá gerar 50 logs a cada 10 segundos e salvar em um arquivo chamado arquivo.log.

Contribuição
Contribuições são bem-vindas! Se você deseja contribuir com este projeto, siga os passos abaixo:

Faça um fork do projeto
Crie um branch para sua feature (git checkout -b feature/nova-feature)
Commit suas mudanças (git commit -m 'Adiciona nova feature')
Faça um push para o branch (git push origin feature/nova-feature)
Abra um Pull Request

```code

Certifique-se de ajustar o conteúdo do arquivo `promtail-config.yaml` conforme necessário e adicionar descrições mais detalhadas sobre como utilizar as funcionalidades específicas do projeto, se necessário.
```
