<img width="3030" height="617" alt="Ilum_Horizontal_monocroma╠ütico branco com assinatura especial_sem fundo" src="https://github.com/user-attachments/assets/6b554e40-defc-485f-8aa4-fe50e052d3ed" />

<h1 align="center"> Estudo da resistência celular em tumores a partir de um modelo de competição de Lotka-Volterra. </h1>

**Alunas:** Ana Luiza de Lima Silva e Mariana Bueno Cavalcanti.

**Turma:** 2026

**Docente responsável:** Prof. Dr. Vinicius F. Wasques

**Disciplina:** Equações diferenciais - 2° semestre de 2026.

**Instituição:** Ilum escola de ciência.

## Informações sobre o respositório
<p align="justify"> Este repositório armazena o código e as figuras desenvolvidas para o trabalho final da disciplina de "Equações diferenciais", ministrada pelo professor Dr. Vinicius F. Wasques no segundo semestre do bacharelado em Ciência e Tecnologia da Ilum escola de ciência. O projeto, desenvolvido a partir do trabalho de McGehee e Mori (2024) [1], busca avaliar quando a terapia adaptativa intermitente aplicada a tumores sólidos é capaz de controlar a resistência celular.

## Sobre o projeto
Na quimioterapia tradicional, o fármaco elimina rapidamente as células sensíveis e libera espaço para as resistentes, que passam a se proliferar. A terapia adaptativa parte da ideia oposta: manter deliberadamente uma população de células sensíveis, que suprime as resistentes por competição. Na terapia intermitente, o fármaco é aplicado até o tumor diminuir a um tamanho pré-definido e suspenso até ele atingir um limite superior.

#### Perguntas do trabalho

Sem fármaco, quem vence a competição entre células sensíveis e resistentes?
O que acontece com uma dose contínua?
A terapia intermitente é capaz de levar à extinção das células resistentes e em quais cenários isso ocorre?

O escopo se restringe à terapia intermitente, com os casos sem fármaco e dose contínua como referências. A terapia adaptativa contínua do artigo não é avaliada.

## O modelo matemático

Competição de Lotka-Volterra entre células sensíveis ($x$) e resistentes ($y$), com populações normalizadas pela capacidade de suporte:

$$
\frac{dx}{dt} = r_x\,x\,(1 - x - \alpha y) - K_A\,r_d\,x \qquad\qquad \frac{dy}{dt} = r_y\,y\,(1 - y - \beta x)
$$

$\alpha$ e $\beta$: intensidade da competição de uma população sobre a outra;
$r_x$ e $r_y$: taxas de crescimento intrínseco;
$r_d$: taxa de morte induzida pelo fármaco, que age apenas sobre as sensíveis;
$K_A\in\{0,1\}$: indica se o fármaco está desligado ou ligado.

#### Terapia intermitente. 
Com $V=x+y$ o volume tumoral total, o fármaco liga quando $V$ atinge $A$ e desliga quando $V$ cai a $A-\delta$ (com $0<\delta<A<1$). Entre os dois limiares, $K_A$ mantém o valor anterior.

#### Cenários de competição
Cenário 1 ($\alpha<1$, $\beta>1$): as sensíveis são as competidoras mais fortes.
Cenário 2 ($\alpha>1$, $\beta<1$): as resistentes são as competidoras mais fortes.

## Abordagens apresentadas 

- Análise analítica: equilíbrios (interseções das isóclinas nulas) e estabilidade local pelos autovalores da matriz Jacobiana;
- Análise numérica: método de Runge-Kutta de ordem 4, passo fixo $\Delta t=0{,}01$, com $K_A$ constante em cada passo, implementado em Python (NumPy e Matplotlib);
- Visualização: séries temporais, planos de fase com isóclinas, campos de direções e trajetórias.

O sistema é não linear e acoplado, e na terapia intermitente $K_A$ depende da própria solução, de modo que as trajetórias são obtidas numericamente.

## Tecnologias utilizadas
O desenvolvimento do projeto se deu com o uso da linguagem de programação Python (3.13.7), contando com as seguintes bibliotecas:

- NumPy (2.2.6): manipulação de arrays e operações matemáticas;
- Pandas (2.3.3): organização dos resultados em tabelas
- Matplotlib (3.10.6): visualizações gráficas

## Acesso ao trabalho
O relatório completo do projeto, apresentando a modelagem matemática, reolução numérica e análise dos resultados, bem como os arquivos necessários à sua importação no Overleaf encontram-se na pasta "Trabalho final". O notebook com a implementação do método de Runge-Kutta e comparação dos cenários de aplicação do fármaco encontram-se na aba "Códigos", enquanto as figuras oriundas dele estão na pasta de "Resultados".

## Resultados

- Sem fármaco, a competição, e não o tamanho inicial das populações, define o vencedor: as sensíveis no Cenário 1 (equilíbrio estável em (1,0)) e as resistentes no Cenário 2 (em (0,1)). Não há coexistência;
- Com dose contínua, o tumor encolhe no início e depois volta à capacidade de suporte, composto apenas por resistentes: o fármaco elimina as sensíveis e remove a pressão competitiva sobre as resistentes (liberação competitiva);
- Com terapia intermitente, no Cenário 1 o tumor se mantém entre $A-\delta$ e $A$ e as resistentes diminuem progressivamente até a extinção. No Cenário 2, o volume deixa de retornar a $A-\delta$, o fármaco permanece ligado e o tumor converge para o equilíbrio apenas com resistentes;
- Em nenhum caso o tumor total se anula: a terapia intermitente controla o tumor, mas não o elimina;
- A eficácia da terapia depende da estrutura competitiva do sistema, e não apenas do esquema de aplicação do fármaco.

## Desenvolvedoras
<table align="center">
  <tr>
    <td align="center">
      <a href="https://github.com/AnaLuizaSilv">
        <img src="https://github.com/AnaLuizaSilv.png" width="115" alt="Ana Luiza">
        <br>
        <sub><b>Ana Luiza de Lima Silva</b></sub>
      </a>
      <br>
      <sub>Estudante de Ciência e Tecnologia – Ilum</sub>
    </td>
    <td align="center">
      <a href="https://github.com/mbuenocavalcanti">
        <img src="https://github.com/mbuenocavalcanti.png" width="115" alt="Mariana Bueno">
        <br>
        <sub><b>Mariana Bueno Cacalcanti</b></sub>
      </a>
      <br>
      <sub>Estudante de Ciência e Tecnologia – Ilum</sub>
    </td>
  </tr>
</table>

## Docente responsável
<td align="center">
  <a href="https://bv.fapesp.br/pt/pesquisador/714274/vinicius-francisco-wasques/">
    <img
      width="115"
      alt="Vinicius Francisco Wasques"
      src="https://github.com/user-attachments/assets/ec7555d9-cfc0-48a9-847a-ce75d5969990"
    />
    <br>
    <sub><b>Vinicius Francisco Wasques</b></sub>
  </a>
  <br>
  <sub>Professor pesquisador - Ilum</sub>
</td>

## Referências bibliográficas

[1] MCGEHEE, Cordelia; MORI, Yoichiro. A mathematical framework for comparison of intermittent versus continuous adaptive chemotherapy dosing in cancer. npj Systems Biology and Applications, v. 10, n. 1, p. 140, 2024. DOI: https://doi.org/10.1038/s41540-024-00461-2.

[2] BOYCE, William E.; DIPRIMA, Richard C. Elementary differential equations and boundary value problems. 10. ed. Hoboken: Wiley, 2012.
