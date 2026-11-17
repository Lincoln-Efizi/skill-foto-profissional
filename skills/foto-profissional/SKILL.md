---
name: foto-profissional
description: Melhora uma foto de celular e deixa com cara de foto profissional, sem mudar nada da cena (mesmo produto, mesmo prato, mesmo cômodo, mesma pessoa). Use quando pedirem "melhore essa foto", "deixa essa foto profissional", "foto para o meu anúncio", "foto do produto para o marketplace", "foto do lanche para o app de delivery", "foto do apartamento para aluguel", "foto de perfil para o LinkedIn", ou digitarem /foto-profissional. Usa a IA da Higgsfield pelo terminal.
---

# Foto profissional

Pega uma foto simples, tirada no celular, e devolve **a mesma foto** com qualidade de estúdio: luz, cor, nitidez e
enquadramento melhores. A regra principal é **não inventar nada**. O produto, a comida, os móveis e o rosto continuam
os mesmos. Foto que promete mais do que entrega vira reclamação de cliente.

## Antes de começar

1. Confira se o CLI da Higgsfield está instalado e logado:
   ```bash
   higgsfield account status
   ```
   - Comando não encontrado: siga o passo de instalação do README deste repositório e pare aqui.
   - `Not authenticated` ou `Session expired`: peça para a pessoa rodar `higgsfield auth login` no terminal dela e esperar
     o login no navegador.
   - `No workspace selected`: rode `higgsfield workspace list` e depois `higgsfield workspace set <id>`.
2. Avise que **cada foto gasta créditos da conta Higgsfield da pessoa**. Se ela pedir várias fotos, diga quantas
   gerações vai fazer antes de começar.

## Passo a passo

1. **Pegue a foto.** Caminho do arquivo no computador (a pessoa pode arrastar a foto para o chat). Olhe a foto antes de
   escrever qualquer coisa: o que é, onde está, o que precisa melhorar (escura, torta, fundo bagunçado, sem foco).
2. **Descubra o tipo** e escolha o comando da tabela abaixo. Se a pessoa disse para onde é a foto (marketplace,
   delivery, aluguel, LinkedIn), use isso. Na dúvida, pergunte **uma vez**, com opções.
3. **Gere a foto melhorada** com a foto original como referência:
   ```bash
   higgsfield generate create gpt_image_2_6 --prompt "<comando da tabela>" --image "<caminho da foto>" --aspect_ratio auto --wait
   ```
   Para **retrato / perfil**, use o modelo que preserva melhor o rosto:
   ```bash
   higgsfield generate create seedream_v5_pro --prompt "<comando da tabela>" --image "<caminho da foto>" --aspect_ratio 3:4 --wait
   ```
4. **Baixe o resultado** ao lado da original, com o sufixo `_profissional` (ex.: `lanche.jpg` → `lanche_profissional.png`).
   O comando imprime a URL do arquivo; pegue a de maior resolução.
5. **Confira antes de entregar.** Compare as duas fotos lado a lado:
   - Os mesmos objetos, na mesma posição? A mesma porção? O mesmo rosto?
   - Se a IA tirou, trocou ou acrescentou alguma coisa, gere de novo reforçando no comando "não altere nada da cena".
   - Ficou com cara de render 3D ou plástico? Gere de novo pedindo "fotografia realista, textura real".
6. **Entregue** o caminho da foto nova e diga em uma frase o que mudou (luz, fundo, cor).

## Comandos por tipo de foto

| Tipo | Comando |
|---|---|
| **Produto** (marketplace, loja) | Melhore esta foto como uma foto profissional de produto para loja online: luz de estúdio suave, cores corretas, nitidez alta, sem ruído e sem desfoque. Mantenha exatamente o mesmo produto, na mesma posição e com o mesmo enquadramento, sem mudar forma, cor, textura ou texto do produto. Fotografia realista. |
| **Comida** (delivery, cardápio) | Transforme esta foto em uma foto profissional de cardápio de delivery, mantendo exatamente a mesma comida, a mesma porção e a mesma embalagem ou prato. Não aumente a porção e não adicione ingredientes. Luz natural suave vinda da lateral, cores reais e apetitosas, textura real. Fotografia realista de comida, sem aparência de plástico ou render 3D. |
| **Imóvel / ambiente** (aluguel, hospedagem) | Melhore a qualidade desta foto como se tivesse sido feita por um fotógrafo profissional de imóveis: luz clara e natural, cores corretas, linhas retas, nitidez, sem ruído e sem desfoque. Não altere nada da cena: os mesmos móveis, objetos, quadros, plantas, piso e janela, na mesma posição e com o mesmo enquadramento. Não aumente o cômodo e não mude a vista da janela. |
| **Retrato / perfil** (LinkedIn, currículo) | Transforme esta foto numa foto de perfil profissional: a mesma pessoa, com o mesmo rosto, luz de estúdio suave no rosto, cores corretas, nitidez e fundo de escritório claro e desfocado. Mantenha exatamente o mesmo rosto e a mesma expressão. Fotografia realista, pele com textura natural, sem retoque exagerado. |

Se a pessoa pedir algo específico (fundo branco, roupa social, arrumar a cama), acrescente ao comando em uma frase curta,
sempre mantendo o "não altere nada da cena" para o resto.

## O que esta skill não faz

- Não cria foto do zero: ela sempre parte da foto que a pessoa mandou.
- Não usa foto de outra pessoa sem que a pessoa da foto tenha autorizado.
- Não coloca logo, marca ou texto de outra empresa na imagem.
