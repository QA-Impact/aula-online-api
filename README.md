
#  Aula Prática: Postman + Newman

Este guia mostra o passo a passo para exportar coleções e ambientes do Postman e executar testes via linha de comando usando **Newman**, incluindo geração de relatórios HTML.

## Etapa 1: Preparar o Postman

### Exportar uma Collection do Postman

1. No Postman, vá até a aba **Collections**
2. Clique com o botão direito na coleção desejada
3. Selecione **Export**
4. Escolha o formato **Collection v2.1**
5. Salve como `minha-colecao.json`

### Exportar as Variáveis de Ambiente

1. No canto superior direito, clique em ⚙️ **Manage Environments**
2. Selecione o ambiente que você criou (ex: `localhost`)
3. Clique nos três pontinhos ao lado → **Export**
4. Salve como `env-localhost.json` ou algo similar


## Etapa 2: Preparar o ambiente Node.js

### Verificar se o Node.js está instalado

```bash
node -v
npm -v
```

Se não estiver, baixe em: https://nodejs.org


##  Etapa 3: Instalar Newman e Reporters

### Instalar o Newman

```bash
npm install -g newman
```

### Instalar o Reporter HTML padrão

```bash
npm install -g newman-reporter-html
```

### Instalar o Reporter HTML avançado (htmlextra)

```bash
npm install -g newman-reporter-htmlextra
```


## Etapa 4: Executar os testes

### Rodar a coleção com Newman

```bash
newman run minha-colecao.json
```

### Rodar com variáveis de ambiente

```bash
newman run minha-colecao.json -e env-localhost.json
```

### Rodar e gerar relatório HTML padrão

```bash
newman run minha-colecao.json -r html
```

### Rodar e gerar relatório HTML bonito com htmlextra 

```bash
newman run minha-colecao.json -e ambiente-qa.json -r htmlextra
```

### Rodar e gerar relatório HTML bonito com htmlextra com opções de pasta e nome do relatório

```bash
newman run minha-colecao.json -e ambiente-qa.json -r htmlextra \
  --reporter-htmlextra-export ./relatorios/relatorio.html \
  --reporter-htmlextra-title "Relatório API"
```

## Dica

Abra o arquivo `relatorio.html` no navegador para visualizar os resultados com detalhes.
