# Visão · TriaSport

> Capacitação em Vibe Coding · Programa de Inovação do Corpo Clínico · Einstein Hospital Israelita
> Documento que define a primeira versão do app. Versão 2, após o parecer final de 05/10/2026.

## Identificação

| Campo | Valor |
|--------------------|------------------------------------------------------------|
| **Nome do app** | TriaSport |
| **Autor** | Dr. Matheus Lorenzetti Peron |
| **Especialidade** | Cardiologia; fellow em Cardiologia do Esporte e do Exercício (IDPC) |
| **Área ou vínculo no Einstein** | Pronto-socorro |
| **Link do app do desafio** | https://triasportapp.netlify.app/ |
| **Data** | 05/10/2026 |
| **Versão** | v2 |
| **Status** | aprovada com recorte leve, parecer de 05/10/2026 |

## 1. Origem da ideia

A ideia nasceu da minha prática em cardiologia do esporte, na avaliação pré-participação de praticantes, sobretudo corredores de rua. As provas oficiais de corrida passaram de 2.827 em 2024 para 5.241 em 2025, alta de 85% (Abraceo), e o mesmo movimento aparece em meia maratona, maratona, HIIT, HYROX, CrossFit e esportes coletivos de alta intensidade.

> "O número de participantes em corridas de rua e esportes amadores cresceu muito, e com ele a população exposta. Cada evento fatal tem grande repercussão pública."

Com mais praticantes, cresce o número de paradas cardíacas em provas, embora a incidência por participante siga estável (RACER, EUA). No consultório, o padrão se repete: há quem chegue ao treino intenso sem avaliação de risco cardíaco e, quando avaliado, receba indicação de exames que muda conforme o médico. O TriaSport começou como triagem do corredor e foi ampliado para a pré-participação em geral.

## 2. O problema

### Quem sofre

- **Paciente:** pratica atividade intensa sem avaliação de risco cardíaco; às vezes investe em treino, tênis e suplementos caros, mas não se avalia e fica exposto à morte súbita e a complicações.
- **Médico ou equipe:** médico de família, generalista, clínico e cardiologista, em dúvida sobre a conduta diante de quem quer se exercitar, sobretudo com intensidade; a dúvida cresce com doença cardiovascular ou sintoma.
- **Família:** no desfecho de morte súbita.
- **Sistema ou instituição:** organizadores oferecem provas sem avaliação médica adequada e temem pela participação de alguns inscritos; o sistema arca com exames sem benefício.

### Como se manifesta

**Variação entre avaliadores.** A pré-participação é o principal instrumento para identificar as cardiopatias associadas à morte súbita no esporte, mas a indicação de exames varia conforme quem avalia.

**Divergência silenciosa entre diretrizes.**

> "As diretrizes divergem entre si (ECG de rotina, cortes etários de história familiar, estratificação do atleta master), e essa divergência raramente fica explícita para quem decide."

**Risco calculado à parte,** em calculadora externa, fora do fluxo da avaliação.

→ **Implicação para o protótipo:** o app responde se o praticante pode treinar e o que investigar antes, e mostra onde as diretrizes divergem e qual posição seguiu.

### O que existe hoje e por que é insuficiente

| O que existe hoje | Limitação principal |
|-------------------------------------------------------|---------------------------------------------|
| Questionários AHA (14 pontos), ESC e ACSM, compilados no IOC Manual, e julgamento de cada médico | A indicação de exames varia conforme quem avalia |
| Checklist impresso, calculadoras isoladas (PREVENT) e autotriagem (PAR-Q+) | Nenhum integra as diretrizes nem mostra onde divergem |

### O que NÃO é o problema

- Não é diagnosticar cardiopatia nem interpretar ECG ou imagem.
- Não é emitir liberação, laudo ou prescrição de treino.

## 3. Solução proposta

### Em uma frase

Apoio à decisão do médico avaliador na pré-participação esportiva: veredito e conduta de exames, cada item com classe, nível e fonte, incluindo o exame sem recomendação formal de rotina; a conduta final é do médico avaliador e sempre individualizada.

### O que entrega

Em poucos cliques, a partir do perfil do praticante, o app diz se ele pode iniciar ou manter o exercício e o que avaliar antes: exame físico, ECG, ecocardiograma, teste ergométrico ou cardiorrespiratório. A indicação sai padronizada pelas diretrizes publicadas: investigação para quem tem critério e nenhum exame sem benefício para quem não tem.

O diferencial está no método: a tela mostra o exame que não se pede, exibe a divergência entre diretrizes, distingue a regra literal da regra interpretada e gera um resumo do caso para o médico.

→ **Implicação para o protótipo:** cada item traz classe, nível e fonte; a faixa "não indicado de rotina" fica visível; as sete interpretações das diretrizes (Anexo A) aparecem marcadas na tela como "interpretação", com a fonte.

### O que NÃO é

- Não é autotriagem: quem usa é o médico. Também não se aplica a menores de 18 anos.
- Não gera papel para o praticante ou o organizador: a ficha é resumo para o médico e não vale como atestado nem como liberação para prova.
- Não calcula o PREVENT, não avalia dieta, não armazena dados nem se integra a sistemas assistenciais.
- Não interpreta exames nem conduz investigação que depende de resultado (angio-TC após TE equívoco, origem anômala de coronária).

### Soluções alternativas exploradas

| Alternativa considerada | Por que ficou fora |
|----------------------------------------|------------------------------------------------------------|
| Longevidade, ergoespirometria em prescrição de treino, ECG do atleta, retorno após evento | A triagem é compreensível para não especialistas e está no meu domínio direto |
| Framingham (ideia inicial) e PREVENT calculado no app | Adotado o PREVENT-DCVA (Dislipidemias 2025), com o valor da calculadora oficial: não reimplemento equação que não posso auditar |
| Eco de entrada único (modelo FIFA) | SBC, ESC e AHA reservam o eco para suspeita clínica |
| Teste funcional em "solicitar" no lazer com risco alto | Nenhuma diretriz o sustenta; no lazer, a idade define o teste (SBC 2019, Tabela 6; ESC 2020, seção 4.2.1) |
| LE8, ficha para o praticante ou o organizador, escore de cálcio e meta de LDL-c | Gap Map: LE8 parcial e fora dos testes; a ficha funcionaria como liberação para prova; cálcio controverso; a meta de LDL-c foge da indicação de exames `[futuro]` |

## 4. Como funciona

### Visão geral

```
Perfil + sintomas + história e exame físico + condições + PREVENT-DCVA
  ↓ sintoma > gatilhos de "completar" > demais (SBC, ESC, AHA/ACC)
Veredito em 3 níveis + conduta em 3 faixas
  ↓ cada item com classe, nível e fonte; interpretação marcada na tela
Notas de divergência + resumo para o médico, com a frase de limitação
```

A avaliação é pontual, sem reclassificação ao longo do tempo.

### Regras essenciais de funcionamento

Todas `[validado]` no parecer de 05/10/2026. Int.: interpretação da diretriz, marcada na tela (Anexo A).

| Regra | Conteúdo |
|------------------|----------------------------------------------------------------------|
| **Não iniciar ou interromper** | Qualquer sintoma de esforço, com precedência absoluta: avaliação cardiológica prioritária, ECG, teste funcional e eco; monitorização do ritmo na síncope ou palpitação. AHA/ACC 2015, SBC 2019 |
| **Completar a avaliação** | Sem sintoma e com ao menos um gatilho: alta intensidade (perfil, intensidade vigorosa ou 6 h/semana ou mais, Int. 2) ou profissional; 60 anos ou mais; aterosclerose documentada ou DCV estabelecida; história familiar pelos 14 pontos (cardiopatia hereditária; morte ou incapacidade cardíaca em parente antes dos 50 anos) ou DAC prematura em parente de primeiro grau (homem antes dos 55, mulher antes dos 65 anos); história pessoal relevante (restrição prévia, exame por suspeita, diagnóstico cardíaco, convulsão inexplicada, cansaço desproporcional aos esforços, queda inexplicada de desempenho, Int. 4); achado de exame físico. Cada gatilho gera ao menos um "solicitar" além do ECG. SBC 2019, ESC 2020, AHA/ACC 2015 e 2018 |
| **Pode iniciar ou manter** | Nenhum gatilho; progressão gradual. Não mudam o veredito: risco alto sem aterosclerose no lazer, PA elevada prévia e obesidade (SBC 2019, Tabela 6; ESC 2020, seções 4.2.1 a 4.2.3); ECG base, itens em "considerar" e risco não estratificado (Int. 7) |
| **Risco** | Dislipidemias 2025, simplificada (Int. 6): PREVENT-DCVA em 10 anos baixo (abaixo de 5%), intermediário (5% a menos de 20%) ou alto (20% ou mais); alto direto na aterosclerose e na hipercolesterolemia familiar. Sem categoria fora de 30 a 79 anos ou com DCV; sem PREVENT nessa faixa, "risco não estratificado" e solicitar a estratificação (Int. 7) |
| **ECG** | Solicitar para todos: I/A no profissional; nos demais, SBC 2019 (Tabela 6), em todas as faixas etárias |
| **Teste funcional** | Solicitar em sintoma, profissional (TE I/C, TCPE I/B), alta intensidade amadora (TE IIa/A, TCPE IIa/C; Int. 1), 60 anos ou mais e aterosclerose documentada; considerar no lazer de 35 a 59 anos (Int. 3); não indicado no lazer abaixo de 35 anos (III/C). TCPE em profissional e carga longa. SBC 2019 (Tabela 6), ESC 2020 |
| **Imagem para DAC** | Considerar imagem funcional ou angio-TC de coronárias em alta intensidade, 35 anos ou mais, risco alto e sem DAC conhecida; sem PREVENT, condicionada à estratificação. ESC 2020, seção 4.2.1 (texto: risco alto e muito alto; quadro: IIb/B no muito alto) |
| **DCV** | Aterosclerose documentada: teste funcional (ESC 2020, seções 5.1.1 e 5.1.2). DAC conhecida: eco em "solicitar" antes de alta intensidade (ESC 2020, seção 5.1.2) e em "considerar" no lazer (Int. 5). DCV não aterosclerótica: avaliação individualizada; considerar teste funcional e eco; com carga longa, solicitar TCPE e eco (SBC 2019, seção 2.3.4; ESC 2020) |
| **Achados de história e exame** | Avaliação cardiológica individualizada; eco em achado de exame físico, exceto PA. Conduta dirigida: rastreamento familiar (suspeita hereditária), raiz da aorta (Marfan), coarctação (pulsos femorais), monitorização do ritmo (ritmo irregular, convulsão) e confirmação de HAS, sem eco (PA elevada; ESC 2020, seção 4.2.3). AHA/ACC 2015, IOC Manual |
| **Ecocardiograma** | Fora das indicações acima, não indicado de rotina; ECG alterado leva a eco, como nota condicional. SBC 2019, ESC 2020, AHA/ACC 2025 |

→ **Implicação para o protótipo:** a etapa 01 perde os campos de eco prévio e de exercício estruturado; a etapa 04 desdobra a DCV em DAC, aterosclerose extracoronária e DCV não aterosclerótica; o PREVENT passa a DCVA em 10 anos, travado em 30 a 79 anos e sem DCV.

### Saída clínica e determinismo

- **Saída do app:** veredito (3 níveis) e conduta (3 faixas: solicitar, considerar, não indicado de rotina), cada item com classe, nível e fonte; a interpretação aparece com a marca "interpretação" e a fonte. Acessórias: notas de divergência e resumo para o médico.
- **Frase de limitação:** no resultado, "Apoio à decisão do médico avaliador. Não substitui a avaliação clínica presencial; a conduta final é do médico."; no texto copiado e no impresso, "Resumo de apoio à decisão. Não é atestado, liberação para prática esportiva ou prova, nem laudo."
- **Lógica determinística:** sim, sem modelo de linguagem; o julgamento clínico entra só na decisão individualizada.
- **Casos sintéticos:** 67 casos em três conjuntos (regra de diretriz, 29; interpretação, 8; valores-limite e invariância, 30), com a saída derivada das regras, não do app atual; viram o arquivo de testes do Spec (`docs/casos-sinteticos.md`). Casos de referência `[validado]`:

| Caso | Entrada | Saída esperada |
|--------|--------------------------------------------|----------------------------------------------------|
| 1 | Mulher, 42 anos, lazer, 4 h/semana, intensidade moderada, até 10 km; sem sintomas, achados ou condições; PREVENT-DCVA 2% | Pode iniciar. Solicitar ECG; considerar TE; eco não indicado de rotina. Nota: a ESC dispensa avaliação adicional (IIa/C) |
| 2 | Homem, 52 anos, alta intensidade, 7 h/semana, meia maratona; sem sintomas, achados ou DAC; PREVENT-DCVA 22% | Completar. Solicitar ECG e TCPE (IIa/C, interpretação); considerar imagem funcional ou angio-TC (ESC 2020); eco não indicado de rotina |
| 3 | Mulher, 50 anos, lazer, intensidade moderada; sem sintomas, achados ou aterosclerose; PREVENT-DCVA 22% | Pode iniciar com progressão gradual. Solicitar ECG; considerar TE; eco não indicado de rotina. No lazer, o risco alto não muda a conduta |

### Núcleo da primeira versão

`[validado]` Parecer de 05/10/2026: veredito e conduta das etapas 01 a 04, com classe, nível e fonte na tela, interpretações marcadas e divergências em nota. Entradas: perfil, sintomas, história e exame físico, condições com a DCV desdobrada e PREVENT-DCVA digitado, com trava. Fica para depois (Gap Map, no Spec): LE8, ficha para o praticante ou o organizador, meta de LDL-c, escore de cálcio, PREVENT calculado no app e reclassificação no tempo.

## 5. Fundamentação e evidência

### Base científica citada

A SBC/SBMEE 2019 é a fonte primária por perfil e idade (Tabela 6); a ESC 2020 refina por volume, risco e DCV; a AHA/ACC dá os 14 pontos (2015) e o contraponto (2025); o ACSM 2015 também não usa o risco calculado como gatilho de teste; a Dislipidemias 2025 classifica o risco pelo PREVENT-DCVA (Khan, 2024).

### Status da evidência no campo

**Status:** em formação `[hipótese]`. Boa parte da triagem é nível C, a imagem é IIb, e as diretrizes divergem no ECG, no teste funcional e na imagem do atleta master.

→ **Implicação para o protótipo:** classe e nível na tela; interpretação marcada, com a fonte; divergências na nota.

### Evidência de resultado

- **Hipótese** `[hipótese]`: o algoritmo melhora a adequação da indicação. A v1 escolhe maior sensibilidade na alta intensidade (ECG e teste funcional para todos) e retira exames sem indicação (eco de rotina, teste no lazer abaixo de 35 anos e pelo risco calculado); o efeito líquido em exames por caso é medido, não assumido.
- **Verificação (Estágio 1):** 100% dos 67 casos sintéticos corretos, inclusive nos valores-limite.
- **Validação (Estágio 2)** `[decisão pendente]`: painel cego de 3 ou mais cardiologistas do esporte em 30 a 40 casos fictícios, com a maioria como referência; meta de 90% de concordância no veredito, kappa por exame e exames por caso comparados ao painel, por estrato de perfil. Na prática do generalista, os mesmos casos sem e com o app `[futuro]`.

## 6. Quem usa, quem decide, quem paga

- **Usuário direto:** o médico avaliador (médico de família, generalista, clínico ou cardiologista).
- **Quem decide a adoção:** `[a confirmar]` A definir com a equipe do Programa.
- **Modelo de adoção:** piloto com casos fictícios; especialistas e, depois, generalistas `[futuro]`.
- **Custos, financiamento e modelo de negócio:** `[futuro]` Fora do escopo nesta fase.

## 7. Bandeiras vermelhas iniciais

- **Clínicos:** falsa tranquilização e delegação da decisão, mitigadas por veredito sem a palavra "liberação", frase de limitação e ficha só para o médico; falso positivo do ECG lido por não especialista `[hipótese]`; risco desconhecido sem PREVENT, mitigado pela estratificação solicitada e pela imagem condicionada ao resultado.
- **CFM:** a decisão final permanece com o médico avaliador.
- **ANVISA:** protótipo sem uso assistencial; em uso assistencial, provável software como dispositivo médico (RDC 657/2022), classe pela RDC 751/2022 `[futuro]`.
- **LGPD:** nenhum dado armazenado; testes só com casos fictícios.
- **Éticos:** interpretação lida como texto literal da diretriz, mitigada pela marca na tela e pelo Anexo A; acesso desigual a TCPE e angio-TC `[hipótese]`.
- **Conteúdo de terceiros:** questionários parafraseados, tabelas não copiadas, PREVENT por link.

## 8. A voz do autor

> "Falta investigação em quem tem critério e sobra exame sem benefício demonstrado em quem não tem." *(sobre o problema)*

> "O diferencial não está na clínica, está no método." *(sobre a solução)*

> "Exibe a divergência entre diretrizes em vez de escolher em silêncio." *(sobre as diretrizes)*

> "Lazer com alto risco: as diretrizes não falam nada para fazer. Se não fala, é porque não precisa; o que conta é a idade." *(sobre o lazer)*

> "Não reimplementa uma equação que não pode auditar (PREVENT)." *(sobre o que NÃO quer)*

## 9. Lacunas e perguntas em aberto

Nenhuma lacuna **[CRÍTICA]** aberta.

1. `[média]` **Painel de validação** `[decisão pendente]`: composição, tamanho e meta; casos reais exigem CEP.
2. `[ação]` **Para o Spec:** Gap Map e Roteiro de Teste; corte de PA no exame e adiamento do teste com PA sistólica acima de 160 mmHg (ESC 2020, seção 4.2.3); mensagem para menores de 18 anos; hipercolesterolemia familiar abaixo de 35 anos no lazer, sem a classe III/C; páginas da SBC 2019 conferidas no PDF.

**Divergências** `[insight]`:

- **ECG para todos:** a SBC o lista em todas as faixas etárias (Tabela 6); a ESC dispensa avaliação adicional no recreativo acima de 35 anos de risco baixo a moderado (IIa/C); a AHA 2025 o considera, sem classe.
- **Teste e imagem:** a ESC poupa o teste no risco baixo a moderado e, no lazer, não o pede pelo risco; considera a imagem no risco alto e muito alto, com IIb/B no quadro para o muito alto; a AHA 2025 dispensa o teste de rotina.

## 10. Referências técnicas

| Fonte | Tipo | Elementos extraídos | Onde |
|---------------------------------------------------------------------|------------|-------------|--------|
| Ghorayeb N, et al. 2019. [Atualização da Diretriz em Cardiologia do Esporte e do Exercício da Sociedade Brasileira de Cardiologia e da Sociedade Brasileira de Medicina do Exercício e Esporte, 2019](https://doi.org/10.5935/abc.20190048). | Diretriz | Classe, Tabela 6 | 4, A |
| Pelliccia A, et al. 2021. [2020 ESC Guidelines on sports cardiology and exercise in patients with cardiovascular disease](https://doi.org/10.1093/eurheartj/ehaa605). | Diretriz | Volume, risco, DCV | 4, A |
| Maron BJ, et al. 2015. [Eligibility and Disqualification Recommendations for Competitive Athletes With Cardiovascular Abnormalities: Task Force 2: Preparticipation Screening for Cardiovascular Disease in Competitive Athletes](https://doi.org/10.1161/CIR.0000000000000238). | Declaração | 14 pontos | 4 |
| Kim JH, et al. 2025. [Clinical Considerations for Competitive Sports Participation for Athletes With Cardiovascular Abnormalities: A Scientific Statement From the American Heart Association and American College of Cardiology](https://doi.org/10.1161/CIR.0000000000001297). | Declaração | Contraponto | 4, 9 |
| Riebe D, et al. 2015. [Updating ACSM's Recommendations for Exercise Preparticipation Health Screening](https://doi.org/10.1249/MSS.0000000000000664). | Consenso | Triagem | 5 |
| Wilson MG, Drezner JA, Sharma S (eds.). 2017. [IOC Manual of Sports Cardiology](https://doi.org/10.1002/9781119046899). | Manual | Questionários | 4 |
| Khan SS, et al. 2024. [Development and Validation of the American Heart Association's PREVENT Equations](https://doi.org/10.1161/CIRCULATIONAHA.123.067626). | Equações | 30 a 79 anos | 4, A |
| Rached FH, et al. 2025. [Diretriz Brasileira de Dislipidemias e Prevenção da Aterosclerose, 2025](https://doi.org/10.36660/abc.20250640). | Diretriz | Risco | 4, A |
| Grundy SM, et al. 2019. [2018 AHA/ACC/AACVPR/AAPA/ABC/ACPM/ADA/AGS/APhA/ASPC/NLA/PCNA Guideline on the Management of Blood Cholesterol](https://doi.org/10.1161/CIR.0000000000000625). | Diretriz | DAC prematura | 4 |
| Kim JH, et al. 2025. [Cardiac Arrest During Long-Distance Running Races](https://doi.org/10.1001/jama.2025.3026). | Registro | Incidência | 1 |
| Abraceo, via Máquina do Esporte. 2026. [Corridas de rua crescem 85% no Brasil em 2025](https://maquinadoesporte.com.br/running/corridas-de-rua-crescem-85-no-brasil-em-2025/). | Dados | Provas | 1 |

## Histórico de versões

| Versão | Data | Principais alterações |
|--------|------------|------------------------------------------------|
| v1 | 30/09/2026 | Documento inicial: Estruturação e decisões do autor de 27 a 30/09/2026. |
| v2 | 05/10/2026 | Parecer final e respostas de 02 e 03/10/2026: LE8 e ficha para o praticante ao Gap Map; regras revistas contra SBC 2019 e ESC 2020; sete interpretações marcadas na tela (Anexo A); sem PREVENT, o veredito não muda; matriz de 67 casos. |

## Glossário de marcações

`[validado]` confirmado · `[decisão pendente]` a decidir · `[ação]` tarefa · `[insight]` do assistente · `[futuro]` fora do escopo · `[a confirmar]` ausente no input · `[hipótese]` especulativo · `[média]` prioridade · **[CRÍTICA]** bloqueia a construção · Int.: interpretação da diretriz, marcada na tela (Anexo A).

## Anexo A · Interpretações das diretrizes

Sete regras aplicam a diretriz por interpretação, não por texto literal. Na tela, levam a marca "interpretação" e a fonte; quando a diretriz traz classe, ela também aparece.

| Nº | Regra | Tipo | Direção | Fonte e leitura |
|------|------------------------------|--------------|--------------|-----------------------------------------------------|
| 1 | Teste funcional em "solicitar" em toda alta intensidade amadora | Classe para faixa | Mais exame | SBC 2019: TE IIa/A e TCPE IIa/C antes de exercício intenso; na Tabela 6, o teste só aparece como "considerar" no lazer de 35 a 59 anos |
| 2 | 6 h/semana ou mais reclassifica para alta intensidade | Harmonização | Mais exame | ESC 2020, seção 3.2: competitivo a partir de 6 h/semana; corresponde ao esportista amador da SBC 2019, que compete eventualmente |
| 3 | Os 35 anos entram na faixa de 35 a 59 | Desempate de fronteira | Mais exame | SBC 2019, Tabela 6: o 35 aparece nas faixas de 18 a 35 e de 35 a 59; ESC 2020, seção 3.1: atleta master a partir de 35 anos |
| 4 | Queda inexplicada de desempenho leva a "completar" | Equivalência de sintoma | Mais restrição | AHA/ACC 2015, 14 pontos: fadiga desproporcional e inexplicada associada ao exercício |
| 5 | Eco em "considerar" na DAC conhecida, no lazer | Extensão | Mais exame; veredito igual | ESC 2020, seção 5.1.2: a função ventricular entra no risco do exercício intenso |
| 6 | PREVENT-DCVA no lugar do SCORE para indicar exame | Adaptação de escala | Estrutural | A Dislipidemias 2025 adota o PREVENT-DCVA; a ESC 2020 liga categoria de risco a exame pelo SCORE. O alto da ESC (SCORE de 5% a menos de 10% de morte CV) equivale a cerca de 15% a 40% de eventos pela conversão da própria ESC, faixa que contém o corte de 20% do PREVENT: aproximação, não equivalência |
| 7 | Sem PREVENT (30 a 79 anos, sem DCV): solicitar a estratificação, sem mudar o veredito | Dado ausente | Veredito igual; um item a mais | Dislipidemias 2025; PREVENT validado de 30 a 79 anos (Khan, 2024). Se o risco alto confirmado não muda a conduta no lazer, o risco desconhecido também não |

*Documento vivo. Tamanho-alvo: 3 a 5 páginas. As marcações permanecem visíveis na versão entregue à equipe.*
