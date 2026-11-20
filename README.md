# Matriz Interativa de Ameacas a Sistemas de Inteligencia Artificial

[![Live Demo](https://img.shields.io/badge/GitHub%20Pages-Live%20Demo-38bdf8?style=for-the-badge)](https://tavardt-portugal.github.io/ai-threat-matrix-pt/)
[![Standard](https://img.shields.io/badge/Standard-OWASP%20LLM%20%26%20MITRE-3b82f6?style=for-the-badge)](https://tavardt-portugal.github.io/ai-threat-matrix-pt/)
[![Privacy](https://img.shields.io/badge/Privacy-100%25%20Client--Side-10b981?style=for-the-badge)](https://tavardt-portugal.github.io/ai-threat-matrix-pt/)
[![License](https://img.shields.io/badge/License-MIT-slate?style=for-the-badge)](LICENSE)

Matriz interativa de ameacas e guia de mitigacao para modelos de linguagem e agentes de IA. Conforme normas OWASP LLM e MITRE ATLAS.

Desenvolvido para organizacoes e equipas tecnicas em **Portugal**, este repositorio disponibiliza uma matriz estruturada para avaliacao de postura defensiva e blindagem tecnica de aplicacoes com Modelos de Linguagem e agentes de Inteligencia Artificial autonomos.

---

## Modos de Operacao

### 1. Aplicacao Web no Navegador (GitHub Pages)
Utilize a aplicacao grafica diretamente a partir do seu navegador:
- **Ligacao Oficial**: [https://tavardt-portugal.github.io/ai-threat-matrix-pt/](https://tavardt-portugal.github.io/ai-threat-matrix-pt/)
- **Privacidade Absoluta**: Processamento 100% no motor JavaScript do navegador. Nenhuma informacao e enviada para servidores remotos.

### 2. Utilitario de Linha de Comandos (CLI)
Para integracao em fluxos de validacao continua (CI/CD) ou utilizacao local no terminal:

```bash
# Avaliacao basica com perfil de agente autonomo
python threat_matrix_evaluator.py --arch agent

# Exportacao de Blueprint de Blindagem em Markdown
python threat_matrix_evaluator.py --arch rag --export-blueprint hardening-blueprint.md

# Validacao rigorosa com ficheiro de perfil
python threat_matrix_evaluator.py --profile profile.json --strict

# Saida estruturada em JSON
python threat_matrix_evaluator.py --arch agent --json
```

---

## 10 Vetores de Ameaca Mapeados (OWASP Top 10 for LLMs)

1. **Injecao de Prompts (Direta e Indireta)**: Manipulacao de instrucoes do LLM via entradas manipuladas ou dados de contexto externo.
2. **Divulgacao de Informacoes Sensiveis**: Fuga involuntaria de dados confidenciais nas respostas geradas.
3. **Vulnerabilidades na Cadeia de Fornecimento**: Riscos decorrentes de bibliotecas externas, plugins vulneraveis ou modelos sem procedencia comprovada.
4. **Envenenamento de Dados e Modeles**: Corrupcao deliberada de dados de treino para induzir comportamentos incorretos.
5. **Tratamento Inadequado de Saidas**: Execucao direta de respostas do modelo por interpretadores ou bases de dados.
6. **Excessiva Concessao de Autonomia**: Agentes dotados de extensoes e permissoes de sistema sem supervisao.
7. **Fuga do Prompt de Sistema**: Extracao nao autorizada de instrucoes confidenciais configuradas no prompt inicial.
8. **Fragilidades em Embeddings e Vetores**: Envenenamento de bases de RAG para desviar respostas do modelo.
9. **Alucinacao e Desinformacao Critica**: Producao de afirmacoes incorretas em fluxos criticos de decisao.
10. **Consumo Ilimitado de Recursos**: Esgotamento de recursos computacionais ou custos descontrolados de tokens.

---

## Integracao com GitHub Actions

```yaml
name: AI Threat Matrix Gate
on: [push, pull_request]

jobs:
  evaluate-ai-security:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Configurar Python
        uses: actions/setup-python@v5
        with:
          python-version: '3.11'
      - name: Executar Avaliacao da Matriz de Ameacas
        run: |
          python threat_matrix_evaluator.py --arch agent --strict
```

---

## Conformidade e Referencial Tecnico

- **Jurisdicao**: Portugal
- **Quadro Normativo**: Referenciais Europeus de Ciberseguranca em IA e OWASP LLM
- **Organizacao Mantenedora**: [TAVARDT-Portugal](https://github.com/TAVARDT-Portugal)

## Portais Institucionais TAVARDT

- **Portal Principal**: [https://ag.tavardt.com/pt/](https://ag.tavardt.com/pt/)
- **Ferramentas de Ciberseguranca**: [https://tools.tavardt.com/pt/](https://tools.tavardt.com/pt/)
- **Contacto Tecnico**: [https://ag.tavardt.com/pt/contato/](https://ag.tavardt.com/pt/contato/)

---

### Licenca
Distribuido ao abrigo da licenca MIT. Consulte o ficheiro [LICENSE](LICENSE) para mais detalhes.
