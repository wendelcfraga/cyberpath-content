# Armazenamento Inseguro em Mobile

Aplicativos móveis frequentemente armazenam dados localmente para melhorar a experiência do usuário ou permitir o uso offline. Se não for feito corretamente, isso pode levar à exposição de dados sensíveis.

## Onde os dados são armazenados?

### Android
1. **SharedPreferences**: Arquivos XML simples usados para armazenar pares chave-valor. Localizados em `/data/data/<package>/shared_prefs/`.
2. **SQLite Databases**: Bancos de dados relacionais estruturados. Localizados em `/data/data/<package>/databases/`.
3. **Internal Storage**: Arquivos privados do aplicativo.
4. **External Storage (SD Card)**: Arquivos que podem ser lidos por qualquer aplicativo com a permissão correta.

### iOS
1. **UserDefaults**: Similar ao SharedPreferences.
2. **Core Data / SQLite**: Armazenamento estruturado.
3. **Keychain**: O local correto para armazenar segredos (senhas, tokens).

## Vulnerabilidades Comuns
- Armazenar senhas ou tokens em texto simples em arquivos XML ou bancos de dados.
- Deixar logs de depuração (Logcat) que contêm informações sensíveis.
- Armazenar dados sensíveis no armazenamento externo.

## Como Prevenir
- **Criptografia**: Usar a **Jetpack Security Library** (EncryptedSharedPreferences/EncryptedFile) no Android.
- **Keychain/Keystore**: Usar os mecanismos nativos do sistema para armazenar chaves e segredos.
- **Não Armazenar**: Se o dado não for estritamente necessário localmente, não o armazene.