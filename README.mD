


## 📊 Repositório de Dados - Produção de Petróleo Petrobras

### 📋 Visão Geral

Este é um repositório corporativo de engenharia de dados estruturado para armazenar, processar e analisar dados de produção de petróleo da Petrobras. Segue as melhores práticas de organização de dados em camadas (raw, processed, staging) para garantir qualidade, rastreabilidade e facilitar análises em diferentes escalas temporais.

### 🏗️ Arquitetura do Repositório

O repositório é organizado em três camadas principais de dados:

| Camada | Diretório | Descrição | Frequência |
|--------|-----------|-----------|-----------|
| **Raw** | `raw/` | Dados brutos e não processados, capturados diretamente das plataformas de produção | Diário |
| **Processed** | `processed/` | Dados validados, limpos e enriquecidos com agregações diárias | Diário |
| **Staging** | `staging/` | Dados agregados mensalmente prontos para warehouse e análises estratégicas | Mensal |

### 📁 Estrutura de Diretórios

```
repositorio_dados_petrobras/
├── raw/                    # Dados brutos sem processamento
├── processed/              # Dados processados e validados
├── staging/                # Dados em transição para warehouse
├── scripts/                # Scripts Python para pipelines ETL/ELT
├── notebooks/              # Jupyter notebooks de análise e exploração
├── config/                 # Arquivos de configuração e variáveis de ambiente
├── logs/                   # Registros de execução e erros
├── tests/                  # Testes unitários e de integração
├── docs/                   # Documentação técnica do projeto
├── models/                 # Modelos de ML e artefatos treinados
├── output/                 # Resultados, exports e relatórios finais
├── metadata.json           # Metadados do projeto
└── .gitignore              # Configuração de arquivos ignorados
```

### 📊 Estrutura dos Dados

#### Dados Brutos (Raw)
- **Arquivo**: `producao_bruta.csv`
- **Registros**: 366 observações diárias
- **Período**: 01/01/2023 a 01/01/2024
- **Colunas**:
   - `data`: Data da medição (datetime)
   - `plataforma`: Identificador da plataforma (P-01, P-02, P-03, P-04)
   - `producao_barris`: Volume de produção em barris (float)
   - `pressao_psi`: Pressão do sistema em PSI (float)
   - `temperatura_celsius`: Temperatura operacional em Celsius (float)
   - `qualidade_api`: Índice de qualidade API do óleo (float)

#### Dados Processados (Processed)
- **Arquivo**: `producao_diaria.csv`
- **Registros**: 366 registros diários
- **Conteúdo**: Agregação de médias diárias por plataforma
- **Uso**: Análises de tendências diárias e detecção de anomalias

#### Dados Staging (Staging)
- **Arquivo**: `producao_mensal.csv`
- **Registros**: 13 períodos mensais
- **Conteúdo**: Agregação mensal com somatórios de produção e médias de parâmetros operacionais
- **Uso**: Relatórios executivos e análises de longo prazo

### 🚀 Como Usar

#### 1. Clonar o Repositório
```bash
git clone <url-do-repositorio>
cd repositorio_dados_petrobras
```

#### 2. Instalar Dependências
```bash
pip install pandas numpy jupyter matplotlib seaborn scikit-learn
```

#### 3. Acessar os Dados
```python
import pandas as pd

# Carregar dados brutos
df_raw = pd.read_csv('raw/producao_bruta.csv')

# Carregar dados processados
df_processed = pd.read_csv('processed/producao_diaria.csv')

# Carregar dados de staging
df_staging = pd.read_csv('staging/producao_mensal.csv')
```

#### 4. Executar Análises
Navegue até a pasta `notebooks/` e execute os Jupyter notebooks disponíveis para análises exploratórias e geração de insights.

### 📈 Métricas-Chave

- **Volume Total de Produção**: ~1.17M barris em 2023
- **Produção Diária Média**: ~3,200 barris/dia
- **Range de Pressão**: 2,000 - 3,500 PSI
- **Range de Temperatura**: 40 - 80°C
- **Qualidade API Média**: ~29.5 graus

### 🔒 Segurança e Privacidade

- Dados sensíveis são mantidos no diretório `raw/` e não são versionados (`.gitignore`)
- Acesso restrito a membros autorizados do projeto
- Logs de auditoria armazenados em `logs/`
- Utilizar `.env` para credenciais e variáveis sensíveis

### 📝 Padrões de Código

- Python 3.8+
- Nomenclatura em snake_case para variáveis e funções
- Documentação em português
- Testes obrigatórios para novos pipelines ETL

### 🤝 Contribuições

Contribuições são bem-vindas! Siga estas diretrizes:

1. Crie uma branch para sua feature (`git checkout -b feature/nova-analise`)
2. Commit suas mudanças (`git commit -m 'Adiciona nova análise'`)
3. Push para a branch (`git push origin feature/nova-analise`)
4. Abra um Pull Request com descrição detalhada

### 📞 Suporte

Para dúvidas ou problemas, abra uma issue no repositório ou entre em contato com o time de dados.

### 📄 Licença

Propriedade da Petrobras - Uso Corporativo

---

**Última Atualização**: 2024 | **Versão**: 1.0