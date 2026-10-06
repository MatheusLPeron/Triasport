# TriaSport · Casos sintéticos v1

> Capacitação em Vibe Coding · Programa de Inovação do Corpo Clínico · Einstein Hospital Israelita
> Autor: Dr. Matheus Lorenzetti Peron · 05/10/2026 · Referência: Visão v2, aprovada com recorte leve (parecer de 05/10/2026)

Matriz de 67 casos com a saída esperada de cada um, derivada das regras da Visão v2. É o Estágio 1 da validação e a base do arquivo de testes do Spec: a meta é 100% de acerto, inclusive nos valores-limite.

**Siglas:** TF, teste funcional · TE, teste ergométrico · TCPE, teste cardiopulmonar · HF, hipercolesterolemia familiar · S, solicitar · C, considerar · NI, não indicado de rotina.

### Como ler

- Cada caso testa uma regra. O conjunto A testa regras de texto literal; o conjunto B, as interpretações do Anexo A da Visão v2; o conjunto C, valores-limite e invariância.
- A saída esperada vem das regras da Visão v2 (parecer de 05/10/2026), não do app atual.
- **ECG:** I/A no profissional; nos demais, SBC 2019 (Tabela 6), sem classe. Na tabela aparece só como "ECG".
- **Nota condicional, válida para todos os casos:** ECG alterado leva a eco.
- **Base** (caso 1 da Visão): mulher, 42 anos, lazer, 4 h/semana, intensidade moderada, carga até 10 km, sem sintomas, sem achados de história ou exame, sem condições, PREVENT-DCVA 2%.
- **Saída da base:** pode iniciar. S: ECG. C: TE. NI: eco. Risco baixo.
- Cada caso lista só o que muda em relação à base.

### Conjunto A · Regras de diretriz

| Caso | Muda na base | Saída esperada | Regra e fonte |
|---|---|---|---|
| A1 | Síncope ao esforço | **Não iniciar.** S: avaliação cardiológica prioritária, ECG, TE, eco, monitorização do ritmo | Precedência do sintoma; AHA/ACC 2015, SBC 2019 |
| A2 | Palpitação ao esforço | **Não iniciar.** S: avaliação prioritária, ECG, TE, eco, monitorização do ritmo | Precedência do sintoma; monitorização |
| A3 | Dor torácica ao esforço | **Não iniciar.** S: avaliação prioritária, ECG, TE, eco. Sem monitorização | Monitorização só com síncope ou palpitação |
| A4 | Profissional, 28 anos, sem PREVENT, dor torácica ao esforço | **Não iniciar**, e não "completar". S: avaliação prioritária, ECG, TCPE, eco | Precedência absoluta sobre o perfil |
| A5 | Profissional, 25 anos, sem PREVENT, maratona | **Completar.** S: ECG (I/A), TCPE (I/B). NI: eco. Risco sem categoria | Perfil profissional; SBC 2019 |
| A6 | 25 anos, sem PREVENT | **Pode iniciar.** S: ECG. NI: TF (III/C), eco. Risco sem categoria | Lazer abaixo de 35 anos; SBC 2019 |
| A7 | Nenhuma (é a base) | **Pode iniciar.** S: ECG. C: TE. NI: eco. Nota: a ESC dispensa avaliação adicional no recreativo acima de 35 anos de risco baixo (IIa/C) | Lazer de 35 a 59 anos; SBC 2019, Tabela 6 |
| A8 | 65 anos, PREVENT 15% | **Completar.** S: ECG, TE. NI: eco. Risco intermediário | 60 anos ou mais; SBC 2019, Tabela 6 |
| A9 | 50 anos, PREVENT 22% | **Pode iniciar com progressão gradual.** S: ECG. C: TE. NI: eco. Risco alto | Lazer com risco alto: o teste segue a idade; SBC 2019, Tabela 6; ESC 2020, seção 4.2.1 |
| A10 | HF, sem aterosclerose | **Pode iniciar com progressão gradual.** S: ECG. C: TE. NI: eco. Risco alto direto | Lazer com risco alto: o teste segue a idade; SBC 2019, Tabela 6; ESC 2020, seção 4.2.1 |
| A11 | 67 anos, PREVENT 25% | **Completar.** S: ECG, TE. NI: eco. Risco alto | O teste vem da idade, não do risco; SBC 2019, Tabela 6. Forma par com A8 |
| A12 | Sopro no exame | **Completar.** S: ECG, avaliação cardiológica individualizada, eco. C: TE | Achado de exame físico; AHA/ACC 2015 |
| A13 | Estigmas de Marfan | **Completar.** S: ECG, avaliação individualizada, eco com avaliação da raiz da aorta. C: TE | Achado de exame físico; AHA/ACC 2015 |
| A14 | Pulsos femorais diminuídos | **Completar.** S: ECG, avaliação individualizada, eco, investigação de coarctação. C: TE | Achado de exame físico; AHA/ACC 2015 |
| A15 | Ritmo irregular no exame | **Completar.** S: ECG, avaliação individualizada, eco, monitorização do ritmo. C: TE | Achado de exame físico; AHA/ACC 2015 |
| A16 | PA elevada no exame | **Completar.** S: ECG, avaliação individualizada, confirmação de HAS. C: TE. NI: eco | Achado de exame físico; ESC 2020, seção 4.2.3 |
| A17 | Irmão com cardiomiopatia hipertrófica | **Completar.** S: ECG, avaliação individualizada, eco, rastreamento familiar dirigido. C: TE | Cardiopatia hereditária na família; AHA/ACC 2015 |
| A18 | Morte súbita de parente aos 40 anos | **Completar.** S: ECG, avaliação individualizada, eco. C: TE | Morte cardíaca antes dos 50 anos; AHA/ACC 2015 |
| A19 | Pai com infarto aos 50 anos | **Completar.** S: ECG, avaliação individualizada. C: TE. NI: eco | DAC prematura (homem antes dos 55); AHA/ACC 2018 |
| A20 | Restrição prévia ao esporte | **Completar.** S: ECG, avaliação individualizada. C: TE. NI: eco. Mesma saída para exame cardíaco por suspeita e diagnóstico cardíaco prévio | História pessoal; AHA/ACC 2015 |
| A21 | Convulsão inexplicada | **Completar.** S: ECG, avaliação individualizada, monitorização do ritmo. C: TE. NI: eco | História pessoal; AHA/ACC 2015 |
| A22 | Cansaço desproporcional aos esforços, como antecedente | **Completar.** S: ECG, avaliação individualizada. C: TE. NI: eco | História pessoal; AHA/ACC 2015 (14 pontos) |
| A23 | PA elevada prévia e obesidade, PREVENT 4% | **Pode iniciar.** S: ECG. C: TE. NI: eco | ESC 2020, seções 4.2.2 e 4.2.3 |
| A24 | 55 anos, aterosclerose carotídea conhecida | **Completar.** S: ECG, TE. NI: eco. Sem imagem (lazer). Risco alto direto; PREVENT não se aplica | ESC 2020, seção 5.1.1 |
| A25 | 55 anos, alta intensidade, DAC conhecida | **Completar.** S: ECG, TE, eco. Sem imagem (DAC conhecida) | ESC 2020, seção 5.1.2 |
| A26 | DCV não aterosclerótica, carga até 10 km | **Completar.** S: ECG, avaliação individualizada. C: TE, eco | ESC 2020, avaliação por cardiopatia |
| A27 | DCV não aterosclerótica, maratona | **Completar.** S: ECG, TCPE, eco, avaliação individualizada | SBC 2019, seção 2.3.4; ESC 2020 |
| A28 | Homem, 52 anos, alta intensidade, 7 h/semana, meia maratona, PREVENT 22% (caso 2 da Visão) | **Completar.** S: ECG, TCPE (IIa/C). C: imagem funcional ou angio-TC. NI: eco | Imagem no risco alto; ESC 2020, seção 4.2.1 |
| A29 | 40 anos, alta intensidade, HF, sem DAC | **Completar.** S: ECG, TE (IIa/A). C: imagem. NI: eco. Risco alto direto | Imagem no alto direto; ESC 2020, seções 4.2.1 e 4.2.4 |

### Conjunto B · Interpretações das diretrizes

| Caso | Muda na base | Saída esperada | Interpretação testada |
|---|---|---|---|
| B1 | Alta intensidade declarada, 30 anos, PREVENT 1% | **Completar.** S: ECG, TE (IIa/A). NI: eco. Sem imagem | 1 · classe para faixa |
| B2 | Homem, 38 anos, alta intensidade, 9 h/semana, maratona (caso 3 da Visão) | **Completar.** S: ECG, TCPE (IIa/C). NI: eco. Sem imagem (risco baixo) | 1 · classe para faixa, na carga longa |
| B3 | Intensidade pretendida vigorosa, perfil lazer | **Completar.** S: ECG, TE (IIa/A). NI: eco | 1 · intensidade vigorosa como alta intensidade |
| B4 | 7 h/semana, perfil lazer | **Completar.** S: ECG, TE (IIa/A). NI: eco | 2 · harmonização do volume |
| B5 | Queda inexplicada de desempenho | **Completar.** S: ECG, avaliação cardiológica individualizada. C: TE. NI: eco | 4 · equivalência de sintoma |
| B6 | 55 anos, lazer, DAC conhecida | **Completar.** S: ECG, TE. C: eco | 5 · extensão ao lazer. Forma par com A25 |
| B7 | PREVENT não informado | **Pode iniciar.** S: ECG, estratificação de risco (PREVENT-DCVA). C: TE. NI: eco. Tela: risco não estratificado | 7 · dado ausente. Mesmo veredito de A9, com risco alto confirmado |
| B8 | Alta intensidade, 45 anos, PREVENT não informado | **Completar.** S: ECG, TE (IIa/A), estratificação de risco. NI: eco. Imagem para DAC condicionada ao resultado da estratificação | 7 · dado ausente em alta intensidade |

As interpretações 3 e 6 são testadas no conjunto C (C1 e C2; C7 a C12) e em A9 e A11.

### Conjunto C · Valores-limite e invariância

| Par | Abaixo do corte | No corte ou acima | O que testa |
|---|---|---|---|
| C1 e C2 | 34 anos: pode iniciar; NI: TF (III/C) | 35 anos: pode iniciar; C: TE | Fronteira dos 35 anos (interpretação 3); o veredito não muda |
| C3 e C4 | 59 anos, PREVENT 10%: pode iniciar; C: TE | 60 anos, PREVENT 10%: completar; S: TE | 60 anos inclusivo; SBC 2019, Tabela 6 |
| C5 e C6 | 29 anos, sem PREVENT: pode iniciar; NI: TF (III/C); risco sem categoria | 30 anos, sem PREVENT: pode iniciar; S: estratificação de risco; NI: TF (III/C) | Trava do PREVENT em 30 anos: muda só o item de estratificação |
| C7 e C8 | 50 anos, PREVENT 4,9%: pode iniciar; risco baixo | 50 anos, PREVENT 5,0%: mesma saída; o rótulo vira intermediário | Invariância: nenhuma conduta usa o intermediário |
| C9 e C10 | 55 anos, PREVENT 19,9%: pode iniciar; C: TE; risco intermediário | 55 anos, PREVENT 20,0%: mesma saída; o rótulo vira alto | Invariância no lazer: o risco alto não muda a conduta |
| C11 e C12 | Alta intensidade, 50 anos, PREVENT 19,9%: completar; S: TE; sem imagem | Mesmo caso, PREVENT 20,0%: igual, com C: imagem | Corte de 20% para imagem |
| C13 e C14 | 5 h/semana: pode iniciar; C: TE | 6 h/semana: completar; S: TE | Volume inclusivo em 6 h (interpretação 2) |
| C15 | Alta intensidade, 30 anos, 10 h/semana, PREVENT 1% | Completar; S: ECG sem I/A, TE | 10 h/semana não vira profissional |
| C16 e C17 | Alta intensidade, carga até 10 km: S: TE | Alta intensidade, meia maratona: S: TCPE | Tipo de TF pela carga |
| C18 e C19 | Alta intensidade, 34 anos, HF: completar; sem imagem | Mesmo caso, 35 anos: completar; C: imagem | Piso de 35 anos da imagem |
| C20 e C21 | Pai com infarto aos 54 anos: completar | Pai com infarto aos 55 anos: pode iniciar | Corte de 55 anos no homem (na mãe, 64 e 65) |
| C22 e C23 | Morte súbita de parente aos 49 anos: completar; S: eco | Morte súbita aos 50 anos: pode iniciar | Corte de 50 anos dos 14 pontos |
| C24 e C25 | 17 anos: sem conduta, mensagem de escopo | 18 anos: roda normalmente | Exclusão de menores de 18 anos |
| C26 | 80 anos, PREVENT digitado 25% | Campo travado, risco sem categoria; completar (60 ou mais); S: ECG, TE | Trava do PREVENT em 79 anos |
| C27 e C28 | Cansaço desproporcional atual, ao esforço (etapa 02): não iniciar | Cansaço desproporcional como antecedente (etapa 03): completar | Fronteira entre sintoma e história |
| C29 e C30 | PA elevada prévia (história): pode iniciar | PA elevada no exame: completar; S: confirmação de HAS; NI: eco | Fronteira entre história e exame |

**Total:** 67 casos (29 de regra de diretriz, 8 de interpretação, 30 de valores-limite e invariância).
