# Dosagem de concreto — método ABCP

Calculadora de traço de concreto pelo método da ABCP, com dosagem pela resistência média (fcj), correção de umidade dos agregados e inchamento da areia. O resultado sai pronto para a obra: sacos de cimento, padiolas ou latas de areia e brita e baldes de água por betonada.

**App:** https://victortlacerda.github.io/dosagem-concreto/

## Arquivos

| Arquivo | Conteúdo |
|---|---|
| `index.html` | App web (HTML, CSS e JavaScript, sem dependências). Abre direto no navegador. |
| `dosagem-concreto-abcp.xlsx` | Mesma dosagem em planilha Excel, com fórmulas, listas de validação e as tabelas do método. |
| `.github/workflows/pages.yml` | Publica o app no GitHub Pages a cada push na `main`. |

## Entradas

- **Concreto:** fck de projeto, desvio padrão Sd (condições A, B ou C da NBR 12655), slump estimado e classe do cimento (CP-25, CP-32, CP-40 ou CP-ARI).
- **Agregados:** tipo de brita (0, 1 ou 2), tipo de areia (fina, média ou grossa), umidade da areia e da brita e coeficiente de inchamento da areia.
- **Obra:** sacos de cimento por betonada, peso do saco de cimento, medida dos agregados (padiola ou lata), volumes da padiola, da lata e do balde e capacidade da betoneira.

## Roteiro de cálculo (por m³ de concreto)

1. **Resistência de dosagem:** fcj = fck + 1,65 · Sd.
2. **Água:** tabela de consumo de água em função do slump e da brita.
3. **Fator a/c:** tabela de a/c em função da resistência e do cimento, lida para o fcj com interpolação linear entre as linhas. Se a tabela do cimento escolhido não alcança o fcj, o cálculo para e avisa.
4. **Cimento:** água ÷ a/c.
5. **Brita:** volume compactado pela tabela em função da brita e do módulo de finura da areia.
6. **Areia:** volume que completa 1 m³ descontando água, cimento e brita (volumes absolutos), convertido para volume aparente.
7. **Umidade:** peso úmido = peso seco × (1 + h), com h sobre a massa seca.
8. **Água a adicionar:** água da tabela menos a massa de água trazida pelos agregados (1 kg = 1 L).
9. **Inchamento:** volume da areia úmida = massa seca ÷ massa unitária × coeficiente de inchamento (NBR 6467). Use 1,00 se a areia for medida seca ou por peso.
10. **Traço por betonada:** quantidades por m³ × (peso do saco ÷ consumo de cimento) × número de sacos, divididas pelo volume da padiola ou lata e do balde.

### Densidades usadas (kg/m³)

| Material | Específica | Unitária |
|---|---|---|
| Cimento | 3150 | — |
| Areia | 2650 | 1500 |
| Brita | 2700 | 1450 |

## Observações

- O coeficiente de inchamento padrão (1,25) é um valor típico. Para uso em obra, determine-o por ensaio.
- As quantidades arredondadas devem ser conferidas com o slump da primeira betonada.
- O app guarda os valores digitados apenas no navegador de quem o usa.
