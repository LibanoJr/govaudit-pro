# 🛡️ GovAudit Pro: Auditoria de Contratos Públicos com IA

> Trabalho de Conclusão de Curso, Pós-graduação em Ciência de Dados e Machine Learning (UniCEUB).
> Projeto acadêmico: os resultados não substituem auditorias oficiais.

## O problema
Contratos públicos com objeto vago ou fornecedores sancionados são sinais clássicos de risco, mas verificar isso manualmente, contrato a contrato, não escala.

## O que a ferramenta faz
- **🕵️ Análise de fornecedores:** verifica o CNPJ nas bases de sanções do governo (CEIS, CNEP e Acordos de Leniência).
- **📊 Monitoramento de contratos:** busca contratos reais pela API do Portal da Transparência.
- **🧠 Classificação de risco com LLM:** o Gemini 2.0 Flash lê o objeto do contrato e classifica o risco jurídico em:
  - 🔴 **ALTO:** objetos vagos, genéricos ou suspeitos
  - 🟠 **MÉDIO:** atenção necessária
  - 🟢 **BAIXO:** objeto claro e bem definido

## Metodologia de análise de risco
A classificação usa dois mecanismos:
1. **Inteligência Artificial (Gemini 2.0 Flash):** análise semântica do objeto do contrato.
2. **Fallback heurístico:** se a IA não responder, regras baseadas no tamanho do texto e no uso de termos genéricos garantem uma classificação.

## Resultados
[Só se houver números reais: contratos analisados, distribuição de risco, 1–2 exemplos. Senão, apague esta seção.]

## Stack
Python 3.9+ · Streamlit · Google Gemini API · API do Portal da Transparência

## Como executar

```bash
git clone https://github.com/LibanoJr/govaudit-pro.git
cd govaudit-pro
python -m venv venv
source venv/bin/activate      # Windows: venv\Scripts\activate
pip install -r requirements.txt
```

Crie um arquivo `.env` na raiz:

```env
PORTAL_KEY=sua_chave_portal_transparencia
GEMINI_API_KEY=sua_chave_google_gemini
```

Execute:

```bash
streamlit run app.py
```

## Limitações
- Depende da disponibilidade e da completude dos dados do Portal da Transparência.
- A classificação do LLM não foi validada contra auditorias reais; serve como triagem, não como conclusão.
