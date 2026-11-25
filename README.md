# KMUSIC

Projeto pessoal de aplicativo de música multiplataforma, com identidade visual própria e foco em reprodução estável, baixo custo e experiência mobile.

## Arquitetura relatada

- Frontend mobile: React Native e Expo (SDK 58 informado no histórico; confirmar no código).
- Backend: Python, com integração a provedores de áudio e uso relatado de yt-dlp.
- Hospedagem: Railway.
- Plataformas pretendidas: Android, iOS e PC/web.
- Priorizar fontes com reprodução autorizada e respeitar as condições de cada provedor.

## Estado do desenvolvimento — 25/11/2026

Os resultados abaixo são registros de sessões anteriores de desenvolvimento, não uma nova execução de testes. O código-fonte ainda não está disponível neste repositório para auditoria.

| Item | Estado relatado |
| --- | --- |
| Backend | 30/30 testes aprovados anteriormente |
| Android | APK ARM64 compilado e instalado em Moto G20 anteriormente |
| Player | Reprodução, pausa, retomada, avanço e fila automática testados |
| Autenticação e acessibilidade | Correções de crashes relatadas |
| Jamendo | Reprodução funcional relatada |
| Outras fontes | Reprodução com falhas; prioridade crítica |
| Barra de navegação Android | Correção de área segura iniciada; nova build pendente |
| iOS e PC | Validação pendente |

## Provedores de música

| Provedor | Situação |
| --- | --- |
| Jamendo | Fonte funcional relatada; manter teste de regressão |
| YouTube / YouTube Music | Backend apresentou exigência de autenticação e falhas de reprodução; avaliar alternativas autorizadas |
| SoundCloud | Integração em avaliação, não confirmada |
| MusicAPI | Integração em avaliação; verificar direitos de reprodução, quotas e custos |

Referências para avaliação: [SoundCloud API](https://github.com/soundcloud/api/releases) e [MusicAPI](https://musicapi.com/).

### Direção proposta

Adotar adaptadores independentes por provedor, normalizar metadados, distinguir catálogo de disponibilidade real de áudio e utilizar fallback apenas quando houver uma fonte autorizada equivalente. Aplicar timeout, cancelamento, cache limitado, circuit breaker e mensagens de erro claras. Nunca deixar o player carregando indefinidamente.

## Segurança e estabilidade

Controles relatados em sessões anteriores, sujeitos a verificação no código:

- Logs com redação de segredos.
- Classificação de erros HTTP 401/500 e tratamento de HTTP 429.
- Circuit breaker e cache limitado a 256 entradas.
- Proteção de operações de escrita.

Requisitos permanentes:

- Manter tokens, chaves, cookies e credenciais fora do Git; usar variáveis de ambiente e armazenamento seguro.
- Aplicar autenticação, autorização por recurso, validação de entrada, rate limiting e proteção contra SSRF nas integrações externas.
- Não incluir dados pessoais, arquivos de sessão, URLs autenticadas ou logs sensíveis neste repositório público.
- Revisar dependências e corrigir vulnerabilidades sem atualizações destrutivas.
- Respeitar limites, autenticação e licenciamento dos provedores.
- Evitar serviços pagos sem aprovação explícita do responsável.

## Roadmap

### P0 — Reprodução e segurança

- [ ] Diagnosticar e corrigir reprodução fora do Jamendo.
- [ ] Implementar timeout e recuperação de erros de reprodução.
- [ ] Avaliar SoundCloud e MusicAPI, incluindo permissões e custo.
- [ ] Investigar cinco vulnerabilidades npm moderadas relatadas anteriormente.
- [ ] Publicar código-fonte sanitizado e documentação de configuração para permitir auditoria.

### P1 — Experiência mobile

- [ ] Validar correção da barra inferior com react-native-safe-area-context.
- [ ] Resolver falhas de compilação nativa relacionadas a caminhos longos no Windows/CMake.
- [ ] Compilar e testar novo APK Android.
- [ ] Validar playlists, favoritos, biblioteca e histórico.
- [ ] Persistir última faixa, posição e fila de reprodução.
- [ ] Testar reprodução em segundo plano, tela bloqueada e controles de mídia.
- [ ] Testar recuperação de conexão e troca entre Wi-Fi e rede móvel.

### P2 — Multiplataforma e acabamento

- [ ] Validar versão PC/web e iOS.
- [ ] Unificar tokens de design, acessibilidade e ergonomia mobile-first.
- [ ] Melhorar letras sincronizadas quando disponíveis legalmente.
- [ ] Adicionar testes automatizados de integração e regressão por provedor.
- [ ] Documentar build, deploy, rollback e diagnóstico de incidentes.

## Critérios de aceitação

Uma versão só deve ser considerada estável após testes reais de busca, reprodução, pausa, retomada, avanço, fila, persistência, navegação, autenticação, perda de conexão e falhas de cada provedor. Registrar plataforma, versão, resultado e evidência dos testes, distinguindo resultados históricos de validações novas.

## Desenvolvimento e publicação

Este README documenta o projeto e suas prioridades. Não representa uma distribuição executável nem comprova que as funcionalidades pendentes já foram implementadas. Instruções de instalação e build devem ser acrescentadas após publicação e revisão do código-fonte.

Projeto de uso pessoal, não comercial. A licença do código ainda não foi definida neste repositório; os conteúdos musicais permanecem sujeitos aos direitos de seus respectivos titulares.
