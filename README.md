
# 📦 Simulação de Parâmetros de Estoque com Python

Este projeto tem como objetivo calcular e visualizar os principais **parâmetros de estoque com reposição contínua** utilizando Python. Com base em dados reais de consumo e custo, é possível obter insights logísticos valiosos para tomada de decisão.

## 🧠 O que são os parâmetros de estoque?

No gerenciamento logístico, é fundamental garantir que os produtos estejam disponíveis na quantidade certa e no momento certo. Os principais parâmetros calculados neste projeto são:

- **Estoque de Segurança (ES):** Quantidade extra mantida para evitar rupturas em caso de variações de demanda ou atrasos no fornecimento.
- **LEC (Lote Econômico de Compra):** Tamanho ideal do pedido que minimiza os custos totais de pedido e armazenagem.
- **Intervalo entre Pedidos:** Tempo, em dias, entre cada nova reposição.
- **Estoque Máximo:** Quantidade máxima esperada em estoque logo após uma reposição.
- **Estoque Médio:** Representa o nível médio de estoque ao longo do tempo. Aqui é calculado com **lógica condicional**, considerando a relação entre o LEC e o estoque máximo.

## 🧰 Bibliotecas Utilizadas

- **Pandas:** Embora neste script não tenha manipulação de DataFrames, é importado para futuros aprimoramentos com tabelas e exportações de dados.
- **NumPy:** Usado para cálculos com alta performance como operações vetoriais.
- **Matplotlib:** Responsável pela criação de gráficos com linhas de referência, proporcionando visualização clara dos níveis de estoque.

## 🚀 Como Executar

1. Instale os pacotes necessários:
   ```bash
   pip install numpy matplotlib pandas
   ```

2. Execute o script com Python 3:
   ```bash
   python parametros_estoque.py
   ```

3. O script imprimirá os parâmetros calculados no terminal e salvará um gráfico `grafico_estoque.png` com a simulação da curva de estoque.

---

## 📐 Fórmulas Utilizadas

**Estoque de Segurança (ES)**  
<br>ES = Z × σ × √LT 
<br>Z: nível de serviço (1.65 para 95%)
<br>σ: desvio padrão da demanda diária
<br>LT: lead time em dias 

**LEC - Lote Econômico de Compras** 
<br>LEC = √(2 × D × S / (H × C)) 
<br>D: demanda anual
<br>S: custo por pedido
<br>H: taxa de armazenagem anual
<br>C: custo unitário do produto 

**Intervalo entre Pedidos** 
<br>Intervalo = LEC / Demanda Diária
**Estoque Máximo (EMAX)** 
<br>ES + Demanda × LT 
**Estoque Médio (condicional)** 
<br>Se LEC ≥ EMAX: ES + (Demanda × LT)/2
<br>Senão: ES + LEC/2 

---

## 🧾 Explicação Técnica do Código

### 1. `calcular_parametros(...)`
Função que recebe os dados do produto (demanda, custo, lead time etc.) e calcula:

- Estoque de Segurança (com nível de serviço de 95%)
- Demanda anual estimada
- Lote Econômico (LEC)
- Intervalo entre pedidos
- Estoque Máximo
- Estoque Médio com **condicional lógica**:
  - Se o LEC for maior que o estoque máximo, o estoque médio é baseado no lead time.
  - Senão, é baseado no LEC.

### 2. `simular_curva_estoque(...)`
- Simula o comportamento do estoque diário ao longo do tempo.
- Adiciona um novo lote (LEC) sempre que o estoque atinge o ponto de reposição.
- Plota a curva e inclui linhas horizontais para os níveis de segurança, médio e máximo.
- O eixo Y é ajustado automaticamente com margem para visualização completa.

---

## 📊 Exemplo de Saída

```
📋 Parâmetros Calculados:
- Estoque de Segurança: 29.52
- LEC (Lote Econômico): 632.46
- Intervalo entre Pedidos (dias): 15.81
- Estoque Máximo: 229.52
- Estoque Médio: 345.74
```

---

## 📄 Licença

Este projeto está sob a licença MIT. Sinta-se livre para usar, modificar e compartilhar.

## 🤝 Contribuição

Contribuições são bem-vindas! Abra uma issue ou envie um pull request.

---

💡 Desenvolvido por Leandro Pereira – Especialista em Logística com Python aplicado à tomada de decisão.
