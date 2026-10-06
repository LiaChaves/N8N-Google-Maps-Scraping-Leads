# 🗺️ Lead Magnet: Google Maps & Decider Enrichment (n8n Workflow)

Fluxo automatizado no **n8n** para prospecção B2B (Lead Magnet). Ele busca empresas no **Google Maps**, valida os resultados com IA, descobre o **nome do decisor** (CEO, Fundador, Sócio), localiza o **LinkedIn** pessoal, busca o **e-mail corporativo** e salva tudo estruturado em uma planilha do **Google Sheets**.

---

## ⚙️ Como o Fluxo Funciona

```text
Formulário de Entrada 
    └── Busca Google Maps (Apify)
       └── Validação do Negócio (OpenAI)
           └── Busca do Decisor (Perplexity + Sonar)
               └── Busca do LinkedIn Pessoal (Tavily AI Agent)
                   └── Busca de E-mail Corporativo (AnyMail Finder)
                       └── Gravação Estruturada (Google Sheets)
```
```
Gatilho (Formulário): Recebe Nicho, Cidade, Estado e Quantidade desejada de leads.

Scraping: O ator da Apify extrai os dados brutos de empresas no Google Maps.

Validação: A IA filtra se a empresa realmente pertence ao segmento solicitado.

Descoberta do Decisor: Agente de IA (Perplexity via Sonar) busca em fontes públicas (QSA, CNPJ, site oficial) o sócio/CEO da empresa.

LinkedIn: Agente com busca web (Tavily) encontra o perfil pessoal do decisor.

Enriquecimento de E-mail: A API da AnyMail Finder busca e valida o e-mail pelo domínio e nome.

Exportação: Insere os dados finais na planilha Google Sheets categorizados pelo nível de enriquecimento atingido.
```
## 🛠️ Pré-requisitos & Ferramentas Utilizadas
```
Para rodar este fluxo, você precisará de uma instância do n8n e contas nos seguintes serviços:

n8n (versão self-hosted ou cloud)

Apify (Ator: compass/crawler-google-places)

OpenAI (Para a tomada de decisão e validação)

Perplexity API (Modelo sonar-reasoning-pro)

Tavily (Pesquisa em tempo real para o Agente)

AnyMail Finder (Enriquecimento de e-mails corporativos)

Google Sheets (Armazenamento dos leads)
```
## 🚀 Como Importar e Usar
```
Baixe o arquivo .json deste repositório.

No seu n8n, clique em Add Workflow > Import from File e selecione o JSON baixado.

Conecte as suas próprias credenciais nos nós indicados:

    Apify

    OpenAI

    Perplexity

    Tavily

    Google Sheets

No nó Keys, preencha sua API Key da AnyMail Finder.

Nos nós do Google Sheets, selecione a sua planilha de destino.

Ative o fluxo e acesse o link gerado pelo nó On form submission para iniciar as buscas.

code Code

---
```
### Dica rápida para o commit:
* Nome do arquivo no repositório: `workflow-google-maps-enrichment.json`
* Mensagem de commit sugerida: `feat: add n8n lead generation and enrichment workflow`