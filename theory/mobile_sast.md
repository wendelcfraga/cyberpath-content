# Análise Estática de Aplicativos Móveis (SAST)

A Análise Estática de Segurança de Aplicativos (SAST) é o processo de examinar o código-fonte ou o binário de um aplicativo sem executá-lo.

## Objetivos da Análise Estática
- Identificar segredos expostos (chaves de API, senhas).
- Encontrar vulnerabilidades lógicas.
- Verificar configurações de segurança no `AndroidManifest.xml`.
- Analisar permissões excessivas.

## Ferramentas Essenciais
- **JADX**: Descompilador de arquivos DEX para código Java/Kotlin legível.
- **APKTool**: Usado para fazer engenharia reversa de APKs, permitindo ver recursos e arquivos SMALI.
- **MobSF (Mobile Security Framework)**: Ferramenta automatizada de análise estática e dinâmica.
- **Dex2jar**: Converte arquivos `.dex` em arquivos `.class` (Java).

## O que procurar no Código
- **Strings**: URLs de servidores de teste, credenciais hardcoded.
- **Configurações de Rede**: Verificar se o tráfego HTTP (não criptografado) é permitido.
- **Exported Components**: Atividades ou serviços marcados como `android:exported="true"` podem ser acessados por outros apps maliciosos.
- **Criptografia Fraca**: Uso de MD5 ou chaves fixas.

## Boas Práticas
- Nunca armazene segredos sensíveis no código.
- Use ferramentas de ofuscação (como o ProGuard/R8) para dificultar a engenharia reversa.
- Realize revisões de código focadas em segurança.