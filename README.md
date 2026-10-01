# Geoportal SEMA-MT para GeoLibre Desktop

Plugin independente para acessar os mosaicos e as bases geográficas públicas do
**Geoportal da Secretaria de Estado de Meio Ambiente de Mato Grosso (SEMA-MT)**
diretamente no **GeoLibre Desktop**.

O plugin organiza, em uma única interface, ferramentas para visualizar camadas
WMS e baixar bases vetoriais WFS sem exigir Python, servidor local, Docker ou
instalação do GeoEcosystem-EE.

## Principais funcionalidades

### Visualização

- catálogo incorporado com **182 camadas WMS**;
- acesso a **47 mosaicos e imagens**, incluindo produtos Sentinel, Landsat,
  SPOT, ResourceSat e modelos de elevação;
- visualização de **135 bases temáticas** publicadas pela SEMA-MT;
- pesquisa por nome técnico ou título;
- filtros por tipo e categoria;
- escolha do sistema de referência da requisição WMS;
- definição da opacidade inicial;
- inclusão das camadas no controle nativo do GeoLibre;
- controle posterior de visibilidade, ordem e transparência.

### Download

- catálogo com **135 bases vetoriais WFS**;
- download em **Shapefile compactado (`SHAPE-ZIP`)**;
- download em **GeoJSON**;
- download da camada completa;
- download pela extensão atualmente visível no mapa;
- download pela extensão dos elementos desenhados no GeoLibre.

> O recorte por extensão utiliza uma caixa envolvente — `BBOX`. Para recorte
> geométrico exato, utilize posteriormente as ferramentas geoespaciais do
> GeoLibre, QGIS, ArcGIS Pro ou GeoEcosystem-EE.

## Instalação

1. Baixe o arquivo disponível em: https://github.com/neurojunior/geoportal-sema-mt-geolibre/blob/main/Geoportal_SEMA_MT_GeoLibre_Plugin_V1_0.zip
2. Abra o **GeoLibre Desktop**.
3. Acesse **Plugins → Gerenciar plugins → Configurações**.
4. Em **Instalar a partir de arquivo**, clique em **Escolher .zip**.
5. Selecione o ZIP do plugin.
6. Ative **Geoportal SEMA-MT** no menu **Plugins**.
7. Abra o painel pelo menu superior **Geoportal SEMA-MT** ou pelo botão **MT**
   exibido sobre o mapa.

## Como visualizar uma camada

1. Abra a aba **Visualização**.
2. Selecione **Mosaicos e imagens**, **Bases temáticas** ou **Todas as camadas WMS**.
3. Utilize os campos de pesquisa e categoria para localizar a informação.
4. Selecione a camada desejada.
5. Ajuste a opacidade inicial e o CRS, quando necessário.
6. Clique em **Adicionar ao mapa**.

A camada será registrada no painel de camadas do GeoLibre, onde poderá ser
ligada, desligada, reordenada e ter sua transparência ajustada.

## Como baixar uma base vetorial

1. Abra a aba **Download**.
2. Pesquise ou filtre a base desejada.
3. Escolha o formato:
   - **Shapefile (.zip)**; ou
   - **GeoJSON**.
4. Escolha a abrangência:
   - **Camada completa**;
   - **Extensão do mapa**; ou
   - **Extensão desenhada**.
5. Clique em **Preparar download oficial**.

O arquivo será solicitado diretamente ao serviço oficial da SEMA-MT.

## Arquitetura

```text
GeoLibre Desktop
       │
       └── Plugin Geoportal SEMA-MT
              ├── Visualização → WMS oficial
              └── Download ────→ WFS oficial
```

O plugin funciona inteiramente dentro do GeoLibre Desktop:

- não executa `main.py`;
- não utiliza backend Python;
- não abre servidor em `127.0.0.1`;
- não exige banco de dados local;
- não modifica o GeoEcosystem-EE;
- não armazena cópias dos mosaicos raster.

## Estrutura do plugin

```text
plugin.json
dist/
├── index.js
└── style.css
README.md
```

## Tecnologias e padrões

- GeoLibre Desktop;
- MapLibre;
- Web Map Service — WMS;
- Web Feature Service — WFS;
- GeoServer;
- Shapefile;
- GeoJSON.

## Fontes oficiais

- [Geoportal SEMA-MT](https://geoportal.sema.mt.gov.br/#/)
- [Página institucional do Geoportal](https://www.sema.mt.gov.br/transparencia/index.php/sistemas/simgeo)
- [Portal de Metadados Geográficos da SEMA-MT](https://geonetwork.sema.mt.gov.br/geonetwork/srv/por/catalog.search#/home)
- [GeoLibre](https://geolibre.app/)

## Escopo e limitações

- A disponibilidade das camadas depende dos serviços oficiais da SEMA-MT.
- Alterações de nomes, endereços ou permissões no GeoServer podem exigir a
  atualização do catálogo incorporado.
- Mosaicos e demais produtos raster são disponibilizados somente para
  visualização remota por WMS.
- O plugin não substitui a conferência dos metadados, da data de atualização e
  das condições de uso de cada conjunto de dados.
- As informações devem ser utilizadas respeitando a finalidade, os termos e as
  políticas estabelecidas pelos respectivos órgãos responsáveis.

## Atualização do catálogo

O catálogo desta versão foi preparado em **1º de outubro de 2026**, a partir
dos serviços WMS e WFS disponibilizados pelo Geoportal SEMA-MT.

## Divulgação

https://github.com/neurojunior/geoportal-sema-mt-geolibre/blob/a64a7cdef162707b5cde4061022625fee8f52dc1/Geoportal%20SEMA-MT%20no%20GeoLibre%20Desktop.png

## Créditos

Projeto independente criado para facilitar o acesso da comunidade geoespacial
às bases públicas disponibilizadas pela SEMA-MT por meio do GeoLibre Desktop.

**Dados e serviços:** Secretaria de Estado de Meio Ambiente de Mato Grosso —
SEMA-MT.

**Aplicação GIS:** GeoLibre Desktop.

## Aviso

Este projeto não representa um produto oficial da SEMA-MT nem do projeto
GeoLibre. Os nomes das instituições e tecnologias são utilizados apenas para
identificar as fontes públicas e o ambiente de execução do plugin.

