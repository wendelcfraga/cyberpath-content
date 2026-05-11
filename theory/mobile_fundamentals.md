# Arquitetura de Segurança Android

O Android foi projetado com segurança baseada em camadas. Cada aplicativo é executado em seu próprio ambiente isolado (sandbox).

## O Modelo de Sandbox
- **UID por App**: Cada aplicativo recebe um ID de usuário (UID) único no sistema Linux subjacente.
- **Isolamento de Processos**: Os processos dos aplicativos não podem interferir uns nos outros por padrão.
- **Permissões de Arquivo**: Os dados de um aplicativo são privados e só podem ser acessados pelo UID correspondente.

## Estrutura de um Aplicativo (APK)
- **AndroidManifest.xml**: Define permissões, componentes e requisitos de hardware.
- **classes.dex**: Código compilado para a Dalvik/ART.
- **res/**: Recursos como imagens e layouts.
- **lib/**: Bibliotecas nativas (C/C++).
- **META-INF/**: Assinatura do aplicativo.

## O Kernel Linux
O Android utiliza o kernel Linux para gerenciar memória, processos e drivers. O kernel também reforça a segurança através do **SELinux** (Security-Enhanced Linux), que impõe controles de acesso obrigatórios sobre todos os processos.

## Inicialização Segura (Verified Boot)
Garante que todo o código executado venha de uma fonte confiável e não tenha sido adulterado desde o último boot.