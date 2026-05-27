# Porto do Itaqui — Web Scraping de Navios

Este projeto coleta (scrape) dados públicos sobre navios no **Porto do Itaqui** nas categorias:
- **Atracados**
- **Fundeados**
- **Esperando**

Os dados são extraídos de uma página web usando **Selenium** (navegador automatizado em modo headless) e processados com **BeautifulSoup**, sendo salvos como **CSV**.

## O que foi feito

1. O script abre a página `https://www.portodoitaqui.com/porto-agora/navios`.
2. Ele localiza seções/containers no HTML por IDs (IDs esperados no site):
   - `atracados`
   - `fundeados`
   - `esperados`
3. Para cada categoria, o script:
   - lê o HTML dessas seções
   - percorre as linhas (`tr`) e células (`td`)
   - monta tabelas com campos como **IMO**, **navio**, **operação**, **DWT**, **carga**, **calado**, **agência** e datas
4. Por fim, grava os resultados em 3 arquivos CSV no mesmo diretório.

## Arquivos do projeto

- `script_porto_itaqui.py`
  - Executa a automação do navegador, faz o parse e salva os CSVs.
  - Importa `selenium`, `chromedriver_autoinstaller`, `BeautifulSoup` e `pandas`.
- `dados_dos_navios_atracados.csv`
- `dados_dos_navios_fundeados.csv`
- `dados_dos_navios_esperando.csv`

## Fonte dos dados

- Página do Porto do Itaqui (Porto Agora — Navios):
  - `https://www.portodoitaqui.com/porto-agora/navios`

## Redação de dados sensíveis

Ao preparar o projeto para compartilhar/publicar, evite incluir informações do seu ambiente local no README/repositório, como:
- **Paths absolutos** (ex.: `/home/...`) usados no `to_csv(...)`
- Identificadores do sistema local (ex.: `getpass.getuser()`)

✅ **Boas práticas**: preferir salvar arquivos com caminhos **relativos** ao diretório do projeto e não depender do nome/usuário do sistema.

## Como executar

No diretório `Porto_do_Itaqui`:
1. Ajuste o ambiente (Python e dependências).
2. Rode:
   - `python script_porto_itaqui.py`

Os CSVs serão gerados/atualizados.

## Campos coletados (visão geral)

- **Atracados**:
  - Berço, IMO, Navio, Operação, Bordo, Compr.(m), DWT, Carga, Quant. carga, Calado, Agência, Última atualização

- **Fundeados**:
  - IMO, Navio, Operação, Comp.(m), DWT, Carga, Quant. carga, Calado, Agência, Última atualização

- **Esperando**:
  - IMO, Navio, Operação, Comp.(m), DWT, Carga, Quant. carga, Calado, Agência, Prev. chegada, Última atualização
