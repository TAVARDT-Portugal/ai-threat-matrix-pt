# Matriz Interativa de Ameaças a Sistemas de Inteligência Artificial

[![Live Demo](https://img.shields.io/badge/GitHub%20Pages-Live%20Demo-38bdf8?style=for-the-badge)](https://tavardt-portugal.github.io/ai-threat-matrix-pt/)
[![Standard](https://img.shields.io/badge/Standard-OWASP%20LLM%20%26%20MITRE-3b82f6?style=for-the-badge)](https://tavardt-portugal.github.io/ai-threat-matrix-pt/)
[![Privacy](https://img.shields.io/badge/Privacy-100%25%20Client-Side-10b981?style=for-the-badge)](https://tavardt-portugal.github.io/ai-threat-matrix-pt/)
[![License](https://img.shields.io/badge/License-MIT-slate?style=for-the-badge)](LICENSE)

Matriz interativa de ameaças e guia de mitigação para modelos de linguagem e agentes de IA. Conforme normas OWASP LLM e MITRE ATLAS.

Desenvolvido para organizações, investigadores e equipas de engenharia em **Portugal**, este repositório disponibiliza uma matriz estruturada para avaliação de postura defensiva e blindagem técnica de modelos de linguagem e agentes autónomos de Inteligência Artificial.

***

## Modos de Operação

### 1. Aplicação Web no Navegador (GitHub Pages)
Aceda à versão gráfica interativa diretamente pelo navegador:
- **Endereço Oficial**: [https://tavardt-portugal.github.io/ai-threat-matrix-pt/](https://tavardt-portugal.github.io/ai-threat-matrix-pt/)
- **Privacidade por Conceção**: Processamento efetuado a 100% no motor JavaScript do seu navegador. Nenhum dado arquitetural ou resultado é enviado para servidores externos.

### 2. Utilitário de Linha de Comando (CLI)
Para validação automatizada em pipelines de CI/CD ou auditorias locais:

```bash
# Avaliação básica com perfil de arquitetura de agente autónomo
python threat_matrix_evaluator.py -arch agent

# Exportação de Blueprint de Blindagem em Markdown
python threat_matrix_evaluator.py -arch rag -export-blueprint hardening-blueprint.md

# Validação com ficheiro de perfil de controlos defensivos
python threat_matrix_evaluator.py -profile profile.json -strict

# Saída estruturada em JSON para automações
python threat_matrix_evaluator.py -arch agent -json
```

***

## 10 Vetores de Ameaça Mapeados (OWASP Top 10 for LLMs)

1. **Injeção de Prompts (Direta e Indireta)**: Manipulação das instruções do LLM via entradas manipuladas ou dados de contexto externo.
2. **Divulgação de Informações Sensíveis**: Fuga involuntária de dados confidenciais ou segredos nas respostas geradas.
3. **Vulnerabilidades na Cadeia de Fornecimento**: Riscos decorrentes de bibliotecas externas, plugins vulneráveis ou modelos sem procedência comprovada.
4. **Envenenamento de Dados e Modelos**: Corrupção de conjuntos de treino ou bases documentais de fine-tuning.
5. **Tratamento Inadequado de Saídas**: Execução sem validação de saídas do LLM por interpretadores de código ou bases de dados.
6. **Excessiva Concessão de Autonomia**: Agentes dotados de extensões e permissões de sistema sem supervisão.
7. **Fuga do Prompt de Sistema**: Extração de regras de negócio e instruções confidenciais do prompt base.
8. **Fragilidades em Embeddings e Vetores**: Injeção de documentos forjados no corpus do RAG para desviar respostas.
9. **Alucinação e Desinformação Crítica**: Geração de afirmações incorretas em fluxos críticos de decisão.
10. **Consumo Ilimitado de Recursos**: Esgotamento de recursos computacionais ou custos descontrolados de tokens.

***

## Integração em CI/CD (GitHub Actions)

Exemplo de pipeline para verificação contínua de postura defensiva:

```yaml
name: AI Threat Matrix Gate
on: [push, pull_request]

jobs:
  evaluate-ai-security:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Set up Python
        uses: actions/setup-python@v5
        with:
          python-version: '3.11'
      - name: Run AI Threat Matrix Assessment
        run: |
          python threat_matrix_evaluator.py -arch agent -strict
```

***

## Conformidade e Padrões Técnicos

- **Jurisdição**: Portugal
- **Padrão Normativo**: OWASP Top 10 for LLM Applications e MITRE ATLAS
- **Organização Mantenedora**: [TAVARDT-Portugal](https://github.com/TAVARDT-Portugal)

## Portais Oficiais

- **Portal Institucional**: [Portal Institucional](https://ag.tavardt.com/pt/)
- **Central de Ferramentas**: [Central de Ferramentas](https://tools.tavardt.com/pt/)
- **Canal de Atendimento e Apoio Técnico**: [https://ag.tavardt.com/pt/contacto/](https://ag.tavardt.com/pt/contacto/)

***

### Licença
Distribuído sob a Licença MIT. Consulte o ficheiro [LICENSE](LICENSE) para mais detalhes.
