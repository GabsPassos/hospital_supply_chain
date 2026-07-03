# 🏥 Auditoria e Análise de Otimização Orçamentária Hospitalar

Como profissional com histórico de atuação na área de logística e supply chain em ambiente hospitalar, utilizei Python e a biblioteca Pandas para conduzir uma análise diagnóstica e um processo de saneamento em uma base histórica de movimentações financeiras de saúde. 

Os dados utilizados neste projeto são reais/simulados e foram obtidos a partir do ecossistema público do **Kaggle** (Hospital Supply Chain Dataset), servindo como base para a resolução de problemas práticos de inteligência de negócios.

---

## 🛠️ O Desafio de Engenharia de Dados: Saneamento de Ruído (Data Cleansing)

O projeto iniciou com uma base macro de 500 registros financeiros divididos em categorias orçamentárias (`Expense_Category`) e descrições técnicas (`Description`). 

Logo na primeira inspeção (Data Profiling), identifiquei uma corrupção severa nos metadados: as categorias estavam completamente desalinhadas com as regras de negócio. Itens críticos de consumo (máscaras) e salários médicos estavam misturados e categorizados de forma caótica (ex: salários classificados como suprimentos e ventiladores pulmonares como pessoal).

### Solução Aplicada:
Desenvolvi uma lógica condicional em Python utilizando o método `.loc` do Pandas, remapeando e reescrevendo a estrutura de dados de forma automatizada:
* `Surgeons' salaries` ➡️ Alinhados 100% para **Staffing**
* `Surgical masks` ➡️ Alinhados 100% para **Supplies**
* `Ventilators` ➡️ Alinhados 100% para **Equipment**

O resultado convergiu em uma matriz limpa, íntegra e auditada, pronta para a tomada de decisões diretas.

---

## 📊 Insights Estratégicos de Negócio (Supply Chain & Finanças)

Após garantir a confiabilidade dos dados, apliquei agregações temporais e setoriais (`.groupby`, `.crosstab` e `.unstack`) que revelaram o real comportamento financeiro da instituição:

1. **O Peso do Capital Humano:** A categoria de **Staffing (Pessoal)** representa o maior centro de custo acumulado do hospital (**$4,37M**), seguida de perto por Supplies ($4,26M) e Equipment ($3,71M).
2. **Dinâmica de Compras por Lote:** Uma descoberta crítica foi que o valor médio de um lançamento de máscaras cirúrgicas ($24.792) equipara-se ao lançamento médio de salários de cirurgiões ($23.915). Isso indica uma prática logística de consolidação de despesas em **grandes lotes de suprimentos**, gerando alto impacto concentrado no fluxo de caixa.
3. **Efeito Cumulativo de Setembro/2025:** Embora meses como Outubro/2024 e Dezembro/2024 tenham registrado os maiores recordes isolados em categorias específicas, **Setembro de 2025 consagrou-se como o mês de maior gasto total da história da operação**. O gráfico de linhas revelou que isso ocorreu por um efeito cumulativo de alta simultânea: todos os setores operaram no teto de gastos no mesmo período.

---

## 🚀 Próximos Passos do Projeto

Este arquivo financeiro abriu as portas da visão macro. O projeto evoluirá para a integração (Data Integration / Joins) de outras 4 bases de dados do ecossistema hospitalar:
* **Inventory Data:** Para cruzar o consumo financeiro de máscaras com os níveis reais de ruptura de estoque.
* **Vendor Data:** Para avaliar se o custo cumulativo de suprimentos está atrelado ao Lead Time (atrasos) de fornecedores específicos.
* **Patient & Staff Data:** Para entender a relação entre a demanda de pacientes e o custo de horas/plantões médicos.
