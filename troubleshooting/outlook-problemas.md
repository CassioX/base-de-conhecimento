# Outlook não envia ou não recebe e-mails

**Categoria:** E-mail · **Nível:** N1/N2 · **Tempo médio:** 15–40 min

## Perguntas iniciais
1. O problema é para enviar, receber ou os dois?
2. O webmail (Outlook na Web / OWA) funciona? *(isola: se o webmail funciona, o problema é no computador)*
3. Aparece alguma mensagem de erro? Pedir print.

## Diagnóstico
| Verificação | Como |
|---|---|
| Internet funciona? | Abrir outro site |
| Outlook está "Offline"? | Barra inferior / guia Enviar/Receber → "Trabalhar Offline" |
| Caixa cheia? | Arquivo → Informações → Ferramentas de Limpeza de Caixa de Correio |
| Mensagens presas na Caixa de Saída? | Anexo grande demais (limite comum: 25–35 MB) |
| Senha expirada? | Testar login no webmail |
| Serviço fora do ar? | Status do provedor (ex.: portal de status do Microsoft 365) |

## Soluções
1. **Desativar "Trabalhar Offline"** e clicar em Enviar/Receber
2. **Remover mensagem travada** na Caixa de Saída (anexo grande → enviar por link do OneDrive/SharePoint)
3. **Reparar a conta**: Arquivo → Configurações de Conta → Reparar
4. **Modo de segurança** (testa se um suplemento causa o problema):
   ```cmd
   outlook.exe /safe
   ```
   Se funcionar → Arquivo → Opções → Suplementos → desativar um por um
5. **Recriar o perfil**: Painel de Controle → Email → Mostrar Perfis → Adicionar novo perfil
6. **Reparar arquivo de dados** (.pst/.ost): executar `scanpst.exe` ou excluir o .ost (é recriado pelo servidor)
7. **Reparar o Office**: Aplicativos → Microsoft 365 → Modificar → Reparo Rápido

## Quando escalar
- Webmail também não funciona → problema no servidor/licença → N2
- E-mails sendo rejeitados (mensagem de "undeliverable"/NDR) → verificar código do erro com N2
- Conta comprometida (envio de spam pelo usuário) → **trocar senha imediatamente**, revogar sessões e escalar para segurança
