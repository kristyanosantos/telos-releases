# Telos

Sistema de peticionamento automatizado para o contencioso trabalhista no âmbito da PGFN, com triagem inteligente, geração assistida por IA e revisão humana antes do protocolo.

---

## Como instalar

### 1. Baixe o instalador

Acesse a [última versão](https://github.com/kristyanosantos/telos-releases/releases/latest) e baixe o arquivo `Telos-Setup-X.X.X.exe`.

### 2. Execute o instalador

Dê duplo clique no arquivo baixado e siga o assistente.

> Se o Windows exibir um aviso de "Editor desconhecido" ou SmartScreen, clique em **Mais informações** → **Executar assim mesmo**. O app não é assinado digitalmente porque é uma ferramenta interna, mas seu código é auditável (veja [Confiança e transparência](#confiança-e-transparência)).

### 3. Abra o Telos

Procure por **Telos** no menu Iniciar ou no ícone criado na área de trabalho.

---

## Primeiro uso — configuração

Após a instalação, abra o app e vá em **Configurações → Credenciais e API**. Você precisa configurar três coisas (uma única vez):

1. **Chave da API Anthropic** — gere em `console.anthropic.com` e cole no campo correspondente. Recomenda-se ativar o **auto-reload** para evitar interrupções.
2. **Credenciais do Google Cloud** — siga as instruções na própria tela; o app explica passo a passo.
3. **Login do PJe** — usuário, senha e segredo TOTP (2FA).

Caso você ainda não tenha o arquivo de **diretrizes institucionais** (`diretrizes_institucionais.txt`), solicite ao desenvolvedor responsável e cole o arquivo na pasta de instalação do app. Sem ele, o Telos funciona normalmente, mas a IA não aplicará as orientações específicas ao redigir.

---

## Atualizações automáticas

O Telos verifica novas versões automaticamente toda vez que é aberto. Quando uma versão mais nova estiver disponível, o app exibirá uma notificação com as novidades — basta clicar em **Atualizar** para baixar e instalar.

---

## Histórico de versões

O histórico completo de mudanças está em [Releases](https://github.com/kristyanosantos/telos-releases/releases). Cada versão inclui:

- O instalador (`.exe`)
- Notas da versão (novidades, correções, mudanças)
- Data de lançamento

---

## Confiança e transparência

O Telos é uma ferramenta pessoal desenvolvida por um procurador para uso próprio e compartilhada com colegas que enfrentam o mesmo tipo de demanda. As versões publicadas neste repositório são geradas a partir do código auditável.

- **Sem coleta de dados:** nenhum dado de processo ou credencial é enviado para servidores externos além dos provedores configurados pelo próprio usuário (Google Cloud, Anthropic, PJe, SAJ).
- **Revisão humana obrigatória:** todas as minutas geradas pela IA passam por revisão antes de qualquer ato processual.
- **Suas credenciais ficam no seu PC:** chaves de API, tokens e configurações pessoais são armazenadas localmente, nunca compartilhadas.
- **Seus dados não treinam IA:** ao seguir a configuração recomendada (Vertex AI + API da Anthropic), os autos, minutas e diretrizes que passam pelo Telos não são usados como material de treinamento pelos provedores.

<details>
<summary><strong>▸ Os dados dos processos são usados para treinar a IA? (resposta detalhada)</strong></summary>

<br>

**Não**, desde que você siga a configuração inicial recomendada (Vertex AI via Google Cloud + API da Anthropic via Console). As duas vias têm políticas explícitas de não-treinamento com dados de clientes em uso comercial:

- **Vertex AI (Google):** a política do Google Cloud é clara — dados de clientes (prompts, respostas, anexos) não são usados para treinar os modelos foundation do Gemini. É um compromisso contratual do *Cloud Data Processing Addendum*. Mais detalhes no [whitepaper de privacidade do Google Cloud](https://services.google.com/fh/files/misc/genai_privacy_google_cloud.pdf).

- **Anthropic via API (Console):** uso comercial via API segue os *Commercial Terms of Service*, que proíbem o uso dos dados para treinamento, sem opção de opt-in. É política distinta (e mais protegida) dos planos consumer do Claude.ai. A retenção padrão dos logs de API é curta (até 30 dias para *abuse-checking*).

Ou seja: enquanto você usar as APIs como recomendado, os autos, minutas e diretrizes que passam pelo Telos não viram material de treino.

> **Importante:** esta resposta é a melhor leitura das políticas dos provedores no momento da redação deste documento. Políticas mudam; se isso é crítico para o seu uso, confira diretamente os termos atuais nos consoles antes de tomar decisões.

</details>

---

## Suporte

- **Manual do usuário:** acessível diretamente na interface do app, em **Ajuda → Manual**
- **Bugs e sugestões:** envie pelo formulário interno do app (**Configurações → Suporte**) ou abra uma [issue](https://github.com/kristyanosantos/telos-releases/issues)

---

## Licença

Projeto pessoal de uso restrito. Distribuição limitada a colegas convidados pelo desenvolvedor. Não constitui produto institucional.
