# 📦 Simulação de Parâmetros de Estoque com Python

Este projeto tem como objetivo calcular e visualizar os principais **parâmetros logísticos de estoque com reposição contínua**, utilizando Python e boas práticas de análise quantitativa. A visualização é feita por meio de **cards gráficos** que tornam a interpretação mais acessível para gestores e equipes operacionais.

---

## 🛍️ Cenário Prático: Papel Sulfite A4

Imagine que você administra uma papelaria. Um dos produtos mais vendidos é o **Papel Sulfite A4**. Com base nos registros do mês, você identificou os seguintes dados:

| Parâmetro | Valor |
|----------|-------|
| Demanda diária | 40 pacotes |
| Desvio padrão | 8 |
| Lead time | 5 dias |
| Custo por pedido | R$ 120 |
| Armazenagem | 20% ao ano |
| Preço unitário | R$ 30 |

A partir desses dados, o script calculará os valores ideais para manter o equilíbrio entre **nível de serviço** e **custos logísticos**, gerando os **cards visuais com os parâmetros** e explicações para leigos.

---

## 🧠 O que são os Parâmetros de Estoque?

Na gestão logística, manter o equilíbrio entre disponibilidade de produtos e controle de custos é essencial. Por isso, este projeto calcula automaticamente os seguintes indicadores:


<br>
ES (Estoque de Segurança)
<br> 
Protege contra variações inesperadas de consumo e atrasos do fornecedor.
<br>
<br>PP (Ponto de Pedido)
<br>Nível do estoque no qual um novo pedido deve ser feito.
<br>EMAX (Estoque Máximo)
<br> Capacidade máxima que o estoque atinge logo após uma reposição.
LEC (Lote Econômico de Compra)
<br> Quantidade ideal para reposição, equilibrando custos de pedido e armazenagem. |
<br> IPD (Intervalo entre Pedidos) 
<br>Quantos dias se passam entre cada nova compra. 

---

## 📐 Fórmulas Utilizadas

Todas as fórmulas são aplicadas conforme a teoria clássica de administração de estoques:

- **Estoque de Segurança (ES)**  
  `ES = z × σ × √LT`  
  Onde:
  - `z`: Nível de serviço (1.65 para 95%)
  - `σ`: Desvio padrão da demanda diária
  - `LT`: Lead time em dias

- **Lote Econômico de Compra (LEC)**  
  `LEC = √(2 × D × S / (H × C))`  
  Onde:
  - `D`: Demanda anual
  - `S`: Custo por pedido
  - `H`: Custo de armazenagem percentual anual
  - `C`: Custo unitário do produto

- **Intervalo entre Pedidos (IPD)**  
  `IPD = LEC / Demanda diária`

- **Estoque Máximo (EMAX)**  
  `EMAX = ES + (Demanda diária × LT)`

- **Estoque Médio (EM)**  
  Se `LEC ≥ EMAX`: `EM = ES + (Demanda × LT)/2`  
  Senão: `EM = ES + LEC/2`  
  Ajustado para nunca ficar abaixo do PP.

- **Ponto de Pedido (PP)**  
  `PP = ES + (Demanda × LT)/2`

---

## 🧰 Bibliotecas Python Utilizadas

Biblioteca | Finalidade |
|------------|------------|
| `NumPy`    | Realiza operações matemáticas com alto desempenho. |
| `Matplotlib` | Cria os gráficos em formato de cards (visual amigável). |
| `Pandas`   | Preparado para futuras extensões com tabelas e bases de dados. |
| `IPython.display` | Exibe explicações amigáveis em Markdown diretamente no Jupyter/Colab. |

---



## 🖥️ Como Executar

Instale as bibliotecas necessárias:

```bash
pip install numpy matplotlib pandas
```

Execute o notebook em um ambiente Jupyter ou Google Colab. Ele calculará os parâmetros, exibirá o gráfico dos cards e imprimirá explicações como estas:

```
- ES: Seu estoque mínimo de segurança deve ser de 29.52 unidades para evitar rupturas.
- PP: Quando seu estoque atingir 200.0 unidades, é hora de fazer um novo pedido.
- EMAX: O máximo de produtos que você deve manter é 229.52 unidades.
- EM: Seu estoque médio ao longo do tempo será de aproximadamente 200.0 unidades.
- LEC: O lote ideal de compra é de 229.52 unidades para equilibrar custos.
- IPD: Você fará um novo pedido a cada 5.74 dias em média.
```

---

## 📄 Licença

Este projeto está sob a [Licença MIT](LICENSE). Sinta-se livre para usar, modificar e compartilhar com atribuição.

---

## 🤝 Contribuição

Contribuições são bem-vindas! Se você tiver ideias de melhorias ou quiser adaptar o projeto a outros contextos logísticos, abra uma *issue* ou envie um *pull request*.

---

## 💡 Desenvolvido por

**Leandro Pereira**  
Especialista em Logística com aplicação prática de Python para resolução de problemas reais na cadeia de suprimentos.
