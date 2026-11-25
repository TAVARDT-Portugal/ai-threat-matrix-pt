# Matriz Interativa de Ameaças a Sistemas de Inteligência Artificial

[![Live Demo](https://img.shields.io/badge/Live%20Demo-GitHub%20Pages-5b3cf5.svg)](https://tavardt-portugal.github.io/ai-threat-matrix-pt/)
[![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

***

Matriz interativa de ameaças e mecanismo de avaliação de postura defensiva para Grandes Modelos de Linguagem e sistemas autônomos de IA projetado pela **TAVARDT**. Fundamentado nas diretrizes do OWASP Top 10 for LLM Applications e no framework MITRE ATLAS, o utilitário avalia vulnerabilidades, quantifica pontuações defensivas e gera planos de ação estruturados.

***

## Capacidades Centrais e Arquitetura de Segurança

* **Modelagem de Postura Sensível à Arquitetura**: Calibra a avaliação de vulnerabilidades em quatro perfis de solução, abrangendo agente autônomo, pipeline RAG, chat interativo e API de backend.
* **Métricas Quantitativas de Blindagem**: Calcula uma pontuação de força defensiva de 0 a 100 pontos baseada em pesos ponderados e estados de mitigação validados.
* **Geração Automatizada de Blueprints**: Produz planos estruturados de hardening em Markdown detalhando deficiências, brechas prioritárias e caminhos determinísticos de correção.

***

## Vetores de Risco e Impacto Operacional

Implementar modelos de linguagem sem modelagem estruturada de ameaças expõe a infraestrutura a envenenamento de dados, explorações laterais e sequestro de contexto. O avaliador mapeia dez vetores críticos de risco através do ciclo de vida operacional da IA:

* **Injeção de Prompts Direta e Indireta (OWASP-LLM01)**: Intercepta alterações adversariais projetadas para subverter diretrizes de sistema ou executar instruções não confiáveis (Peso: 15 pontos).
* **Divulgação de Informações Sensíveis (OWASP-LLM02)**: Sinaliza vazamentos acidentais de dados pessoais, parâmetros confidenciais e contexto de negócios nas respostas (Peso: 12 pontos).
* **Vulnerabilidades na Cadeia de Suprimentos (OWASP-LLM03)**: Audita dependências de modelos base de terceiros, plugins não auditados e conjuntos externos de dados de ajuste fino (Peso: 10 pontos).
* **Envenenamento de Dados e Modelos (OWASP-LLM04)**: Identifica riscos nos quais dados corrompidos de treinamento ou recuperação comprometem a integridade do modelo (Peso: 10 pontos).
* **Tratamento Inadequado de Saídas (OWASP-LLM05)**: Avalia saídas brutas do modelo enviadas sem sanitização para interpretadores, navegadores ou shells de sistema (Peso: 12 pontos).
* **Agência e Permissões Excessivas (OWASP-LLM06)**: Mitiga agentes superprivilegiados com capacidade de executar comandos destrutivos ou transações sem controle (Peso: 14 pontos).
* **Extração do Prompt de Sistema (OWASP-LLM07)**: Detecta consultas manipulativas formuladas para revelar regras proprietárias de governança e prompts internos (Peso: 8 pontos).
* **Fragilidades em Vetores e Embeddings (OWASP-LLM08)**: Avalia o envenenamento de índices semânticos e recuperação desprotegida em bancos de dados vetoriais (Peso: 7 pontos).
* **Alucinação e Desinformação (OWASP-LLM09)**: Identifica respostas factualmente infundadas que carecem de validação e âncoras de citação confiáveis (Peso: 6 pontos).
* **Consumo Ilimitado de Recursos (OWASP-LLM10)**: Previne condições de negação de serviço provocadas por expansão abusiva de contexto ou loops recursivos de agentes (Peso: 6 pontos).

A postura composta é classificada em **HARDENED** (85 a 100), **DEVELOPING** (60 a 84) ou **VULNERABLE** (abaixo de 60). Vetores defendidos recebem pontuação integral, controles parciais recebem 50% do peso, e exposições não mitigadas pontuam zero.

***

## Instalação e Execução CLI

Avalie a postura de segurança localmente ou integre rotinas de governança automatizadas utilizando suporte nativo em Python:

```bash
# Clonar o repositório oficial
git clone https://github.com/TAVARDT-Portugal/ai-threat-matrix-pt.git

# Acessar o diretório de trabalho
cd ai-threat-matrix-pt

# Avaliar postura utilizando perfil de agente autônomo
python threat_matrix_evaluator.py -a agent

# Exportar plano estruturado de blindagem em Markdown
python threat_matrix_evaluator.py -a agent -e blueprint.md

# Executar avaliação estrita com emissão de dados JSON
python threat_matrix_evaluator.py -a agent -s -j
```

***

## FAQ Técnico

### Qual metodologia a Matriz de Ameaças de IA utiliza para avaliar a postura do modelo?

O mecanismo de avaliação mapeia controles defensivos nas dez categorias do OWASP Top 10 para LLMs através de coeficientes de risco ponderados que totalizam 100 pontos. Com base nos estados validados, a ferramenta classifica a infraestrutura em HARDENED para 85 pontos ou mais, DEVELOPING entre 60 e 84 pontos, ou VULNERABLE abaixo de 60.

### Como os perfis arquiteturais influenciam a análise de risco na ferramenta?

O utilitário CLI ajusta o contexto da avaliação considerando quatro perfis arquiteturais distintos, abrangendo agente autônomo, pipeline RAG, chat interativo e interface API. A seleção do perfil adequado através da opção -a assegura que as medidas corretivas atendam aos fluxos de dados específicos da solução analisada.

### Como o gerador de blueprints auxilia as equipes de engenharia na remediação de falhas?

A execução do avaliador com o parâmetro -e exporta um plano de blindagem estruturado em Markdown com o diagnóstico de exposições e ações corretivas para cada vetor. Esse documento vincula a auditoria de segurança à esteira de engenharia estabelecendo prioridades claras de remediação.

### Quais riscos operacionais decorrem de agência e permissões excessivas (LLM06)?

Conceder permissões excessivas a agentes autônomos possibilita que injeções indiretas de prompt disparem ações não autorizadas em sistemas integrados e bancos de dados. A aplicação de listas estritas de permissões e pontos de confirmação humana restringe a autoridade operacional do modelo ao princípio do menor privilégio.

### O avaliador de postura pode atuar como portão automatizado de qualidade em CI/CD?

A ferramenta processa perfis customizados em formato JSON via opção -p e interrompe a execução com código de saída 1 quando a opção estrita -s detecta vetores expostos. Em conjunto com a flag -j para emissão de dados JSON estruturados, equipes de DevOps podem automatizar o bloqueio de compilações vulneráveis.

***

## Links Úteis

* **Portal Corporativo:** https://ag.tavardt.com/pt/
* **Suíte de Diagnósticos:** https://tools.tavardt.com/pt/
* **Contacto Técnico:** https://ag.tavardt.com/pt/contacto/

***

### Licença
Distribuído sob a Licença MIT. Consulte [LICENSE](LICENSE) para obter detalhes completos.

***

© 2026 TAVARDT. Todos os direitos reservados.
