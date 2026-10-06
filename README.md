[README.md](https://github.com/user-attachments/files/33083319/README.md)
# TriaSport

Apoio à decisão do médico avaliador na avaliação cardiovascular pré-participação esportiva.

O app recebe:

- o perfil do praticante;
- os sintomas de esforço;
- a história e o exame físico;
- as condições clínicas;
- o risco PREVENT-DCVA, que o médico calcula na ferramenta oficial da AHA e digita no app.

Com isso, o app indica:

- **Veredito em três níveis:** pode iniciar, completar a avaliação, ou não iniciar até avaliação cardiológica.
- **Conduta de exames em três faixas:** solicitar, considerar ou não indicado de rotina. Cada item traz classe, nível de evidência e fonte.

Quando uma regra interpreta a diretriz em vez de transcrevê-la, ela aparece marcada como "interpretação". As divergências entre diretrizes ficam visíveis em nota.

## Links

- **App publicado:** https://triasportapp.netlify.app/
- **Visão v2** (aprovada com recorte leve, parecer de 05/10/2026): [docs/visao-peron-v2.md](docs/visao-peron-v2.md)
- **Casos sintéticos** (67 casos com a saída esperada): [docs/casos-sinteticos.md](docs/casos-sinteticos.md)

## Fontes principais

- Atualização da Diretriz em Cardiologia do Esporte e do Exercício da SBC e da SBMEE, 2019
- 2020 ESC Guidelines on sports cardiology and exercise in patients with cardiovascular disease
- AHA/ACC: questionário de 14 pontos (2015) e declaração científica de 2025
- ACSM: recomendações de triagem pré-participação (2015)
- Diretriz Brasileira de Dislipidemias e Prevenção da Aterosclerose, 2025, com as equações PREVENT (Khan et al., 2024)

## Limites

- Uso exclusivo do médico avaliador. Não é autotriagem e não se aplica a menores de 18 anos.
- Não emite atestado, liberação para prática esportiva ou prova, nem laudo. A conduta final é do médico.
- Lógica determinística, sem modelo de linguagem: a mesma entrada gera sempre a mesma saída.
- Protótipo acadêmico. Nenhum dado é armazenado; use apenas casos fictícios.

## Autoria

Dr. Matheus Lorenzetti Peron, cardiologista, fellow em Cardiologia do Esporte e do Exercício (IDPC).

Projeto da Capacitação em Vibe Coding do Programa de Inovação do Corpo Clínico do Einstein Hospital Israelita, 2026.
