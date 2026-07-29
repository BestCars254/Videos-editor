# Videos-editor

Meu editor de vídeos por conversa, rodando com o Claude Code — baseado no
[video-use](https://github.com/browser-use/video-use) (open source, MIT).

Eu jogo os vídeos brutos numa pasta, converso com o agente pedindo as edições,
e recebo o `final.mp4` de volta. Serve pra qualquer conteúdo — cabeça falante,
montagem, tutorial, viagem, entrevista — sem presets nem menus.

## O que ele faz

- **Corta vícios de fala** (`é`, `hum`, começos falsos) e o silêncio entre as tomadas
- **Faz color grading** automático em cada segmento
- **Aplica fades de 30ms** em cada corte pra você nunca ouvir um "pop"
- **Queima legendas** no seu estilo (por padrão, blocos de 2 palavras em MAIÚSCULA)
- **Gera animações de overlay** (Manim, PIL, HyperFrames, Remotion)
- **Se auto-avalia** no resultado renderizado antes de te mostrar
- **Guarda a memória da sessão** em `project.md` pra continuar de onde parou

## Como usar

Nesta sessão já está tudo instalado e a skill `video-use` registrada. Para editar:

1. **Coloque seus vídeos numa pasta** (ex.: `videos/`).
2. **Me peça a edição em português mesmo**, por exemplo:
   - *"edita esses vídeos num vídeo de lançamento"*
   - *"faz o inventário dessas tomadas e me propõe uma estratégia"*
   - *"corta os silêncios e os 'é/hum' e queima legenda"*
3. Eu leio o material, proponho uma estratégia, **espero seu OK**, e produzo o
   `edit/final.mp4` ao lado dos seus vídeos.

Todas as saídas ficam em `<pasta_dos_videos>/edit/` — o repositório fica limpo.

## O que já está pronto neste ambiente

- ✅ `ffmpeg` e `ffprobe` instalados
- ✅ Dependências Python instaladas em `.venv/` (requests, librosa, matplotlib, pillow, numpy)
- ✅ Skill `video-use` registrada no Claude Code
- ⚠️ **Falta a chave da ElevenLabs** (só ela transcreve — timestamps por palavra,
  separação de quem fala, marcação de vícios de fala). Sem ela nada é transcrito.

### Colocar a chave da ElevenLabs

Pegue uma chave em [elevenlabs.io/app/settings/api-keys](https://elevenlabs.io/app/settings/api-keys)
e cole no arquivo `.env` (que não vai pro Git):

```bash
echo 'ELEVENLABS_API_KEY=sua_chave_aqui' > .env
```

Ou me mande a chave no chat que eu escrevo pra você.

> **Atenção:** o ambiente remoto é efêmero. As instalações (ffmpeg, `.venv/`) e a
> sua chave `.env` valem só para esta sessão; se abrir uma nova, é só me pedir
> "prepara o editor de novo" que eu reinstalo. O código versionado (helpers,
> SKILL.md) fica salvo no repositório.

## Documentação

- [`SKILL.md`](./SKILL.md) — regras de produção e o "como editar" completo (o que o agente lê)
- [`install.md`](./install.md) — instalação do zero em outra máquina
- [`README_video-use.md`](./README_video-use.md) — README original do projeto
- [`helpers/`](./helpers/) — os scripts de edição (transcribe, render, timeline_view, grade…)

---

Baseado em [browser-use/video-use](https://github.com/browser-use/video-use) · Licença MIT (ver [`LICENSE`](./LICENSE)).
