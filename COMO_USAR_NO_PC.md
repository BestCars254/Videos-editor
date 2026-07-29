# Como editar meus vídeos no PC (Windows)

> **Por que no PC?** O Claude Code na nuvem tem firewall que bloqueia o download
> do Drive e a transcrição (ElevenLabs), e não enxerga os arquivos do seu `C:\`.
> No PC não tem firewall e o vídeo já está local — tudo funciona.

Meu vídeo de exemplo está em:
`C:\Users\conta\Downloads\Youtube\10,000kcal\10,000kcal.MOV`

## 1. Instalar o Claude Code no Windows

Siga: https://docs.claude.com/en/docs/claude-code/setup
(No Windows funciona nativo ou via WSL. Faça login com a mesma conta.)

## 2. Instalar o ffmpeg (obrigatório) no Windows

No PowerShell:
```powershell
winget install ffmpeg
```
(Feche e reabra o terminal depois, pra o `ffmpeg` entrar no PATH. Teste com `ffmpeg -version`.)

## 3. Baixar meu editor (este repositório)

```powershell
cd $HOME\Downloads
git clone https://github.com/bestcars254/videos-editor
cd videos-editor
```

## 4. Preparar o editor

Abra o Claude Code nessa pasta:
```powershell
claude
```
E diga:
> Leia o install.md e prepare o editor: instale as dependências Python e configure minha chave da ElevenLabs.

Quando ele pedir, cole sua chave da ElevenLabs (pegue em
https://elevenlabs.io/app/settings/api-keys). Ela é gravada em `.env` (fora do Git).

## 5. Editar o vídeo

Ainda no Claude Code, diga (ajuste o caminho se mudar de vídeo):
> Edite o vídeo em "C:\Users\conta\Downloads\Youtube\10,000kcal\10,000kcal.MOV":
> corte os silêncios e os vícios de fala ("é", "hum"), faça um color grade leve e
> queime legenda. Me mostre um preview antes do final.

O resultado sai em uma subpasta `edit/` ao lado do vídeo:
```
10,000kcal\
├── 10,000kcal.MOV        ← original (intacto)
└── edit\
    ├── preview.mp4
    └── final.mp4         ← vídeo editado
```

## Dicas

- **Não precisa subir nada pro Drive nem pro GitHub** — o vídeo fica no PC.
- Você fala com o editor **em português** normalmente.
- Frases boas pra começar: *"faz o inventário e me propõe uma estratégia"*,
  *"corta os silêncios e bota legenda"*, *"deixa em formato vertical pro Reels"*.
- A chave da ElevenLabs que você colou no chat da nuvem: por segurança, **gere uma
  nova** no painel deles e use essa no PC.
