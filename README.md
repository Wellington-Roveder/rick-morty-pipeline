# 🧬 Rick and Morty Data Automation — API to Excel

> Projeto de aprendizado desenvolvido em **Janeiro/2026** — base para a construção do [SentinelLog](https://github.com/Wellington-Roveder/SentinelLog--game-price-monitor).

---

## 📌 Descrição

Este projeto automatiza a extração, tradução e formatação de dados da API pública do Rick and Morty. Ele consome informações de personagens, realiza o tratamento dos dados (incluindo a tradução de termos técnicos para o português) e gera um relatório profissional em Excel com formatação automática.

O objetivo foi aprender na prática como estruturar um modelo base de consumo de API REST, aplicando conceitos de Arquitetura Limpa e Modularização — garantindo que cada parte do sistema (API, Regras de Negócio e Saída de Dados) seja independente.

---

## 🚀 Diferenciais Técnicos

**Consumo Inteligente de API** — uso de `requests.Session()` no `APIClient` para reutilizar conexões HTTP, tornando as requisições mais rápidas e eficientes.

**Tratamento e Tradução** — o `personagem_service.py` atua como um adaptador, transformando o JSON bruto da API em um formato amigável, traduzindo categorias como status, gênero e espécies. A URL da API é centralizada aqui para não espalhar referências pelo projeto.

**Excel Profissional** — o relatório não é apenas uma tabela bruta. O `excel_service.py` utiliza a biblioteca `openpyxl` para:
- Auto-ajustar a largura das colunas conforme o conteúdo
- Aplicar filtros automáticos no cabeçalho
- Congelar a primeira linha para facilitar a leitura de grandes volumes de dados
- Estilizar o cabeçalho em negrito

---

## 📸 Prints da Execução

![Demonstração da Execução](assets/criando_o_excel.png)
![Demonstração da Execução](assets/excel_formatado.png)

---

## 📂 Estrutura do Projeto

```
├── api/
│   └── client.py              # Cliente HTTP customizado com Session e Timeout
├── services/
│   ├── excel_service.py       # Lógica de geração e estilização do Excel
│   └── personagem_service.py  # Regras de negócio, tradução e mapeamento de dados
├── utils/
│   └── logger.py              # Configurações de monitoramento do sistema
├── main.py                    # Ponto de entrada — orquestração do fluxo
└── relatorio_api_exemplo.xlsx # Exemplo de saída gerada
```

---

## ⚙️ Como Executar

```bash
# Clone o repositório
git clone https://github.com/Wellington-Roveder/rick-morty-pipeline.git

# Crie e ative sua venv
python -m venv .venv
.venv\Scripts\activate

# Instale as dependências
pip install pandas requests openpyxl

# Execute
python main.py
```

---

## 🔄 Fluxo Completo

```
main.py
  ↓
APIClient (busca dados da API)
  ↓
dados JSON
  ↓
personagem_service (trata e traduz os dados)
  ↓
excel_service (formata e gera o arquivo)
  ↓
arquivo.xlsx
```

---

## 🎯 Objetivos Alcançados

**Clean Code** — organização modular para evitar acoplamento entre camadas.

**Data Transformation (ETL)** — extração de dados brutos (JSON) e transformação para um formato de negócio (Excel).

**Eficiência de Rede** — gerenciamento de sessões HTTP e timeouts para robustez do sistema.

---

## 🐛 Dificuldades e Aprendizados

**Estruturar o Excel com openpyxl** — exigiu bastante pesquisa na documentação para implementar auto-ajuste de colunas, filtros e formatação de forma funcional dentro do projeto.

**Integração com WhatsApp** — tentei conectar o fluxo à WhatsApp Business API para enviar o relatório automaticamente, mas encontrei limitações técnicas que ficaram como melhoria futura.

---

## 🔮 Melhorias Futuras

- [ ] Logging profissional com rotação de arquivos substituindo os `print()`
- [ ] Paralelismo para processar múltiplas páginas da API simultaneamente
- [ ] Integração com WhatsApp Business API para envio automático do relatório
- [ ] Adaptar o modelo ETL para APIs de nichos financeiros ou logísticos

---

## 📈 Evolução

Este projeto foi o ponto de partida. Os conceitos aprendidos aqui — consumo de API, modularização e ETL — foram evoluídos no **SentinelLog**, onde adicionei banco de dados com histórico, API própria com FastAPI, automação com N8N, logger profissional com rotação diária e alertas por email.

👉 [Ver SentinelLog — o projeto seguinte](https://github.com/Wellington-Roveder/SentinelLog--game-price-monitor)

---

## 👤 Autor

Feito por **Wellington Roveder**
Estou em busca de oportunidades como Desenvolvedor Estagiário/Júnior — feedbacks são bem-vindos!

[LinkedIn](https://www.linkedin.com/in/wellington-roveder-04637b37b/) • [GitHub](https://github.com/Wellington-Roveder)
