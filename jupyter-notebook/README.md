# Jupyter local com Docker

Ambiente JupyterLab conteinerizado para executar os notebooks deste diretório.
O serviço escuta somente em `127.0.0.1` e, portanto, não é publicado para
outros dispositivos da rede. A autenticação por token e senha está desativada.

## Iniciar

```bash
docker compose up -d --build
```

Acesse <http://localhost:8888/lab>. Os arquivos criados pela interface ficam
persistidos em [`notebooks/`](notebooks/).

Para acompanhar a inicialização:

```bash
docker compose logs -f jupyter
```

Para parar o ambiente sem apagar os notebooks:

```bash
docker compose down
```

## Pacotes Python adicionais

Inclua os pacotes em [`requirements.txt`](requirements.txt), um por linha, e
reconstrua o ambiente:

```bash
docker compose up -d --build
```

A imagem base `scipy-notebook` já traz o ecossistema científico mais comum,
incluindo NumPy, pandas, SciPy, Matplotlib, seaborn e scikit-learn.

## Observação de segurança

Como não há autenticação, mantenha o vínculo da porta como
`127.0.0.1:8888:8888`. Alterá-lo para `8888:8888` ou `0.0.0.0:8888:8888`
pode expor o Jupyter e permitir execução de código por outras máquinas.

