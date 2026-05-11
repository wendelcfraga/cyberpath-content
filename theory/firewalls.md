# Configuração de Firewalls

Um firewall é um dispositivo de segurança de rede que monitora o tráfego de rede de entrada e saída e decide se permite ou bloqueia tráfego específico com base em um conjunto definido de regras de segurança.

## Como Funciona
Os firewalls estabelecem uma barreira entre redes internas confiáveis e redes externas não confiáveis, como a Internet.

## Tipos de Firewalls

### 1. Filtragem de Pacotes
O tipo mais básico, que analisa pacotes e os bloqueia com base em endereços IP, protocolos e portas.

### 2. Inspeção de Estado (Stateful Inspection)
Monitora o estado das conexões ativas e utiliza essas informações para determinar quais pacotes de rede permitir através do firewall.

### 3. Firewalls de Próxima Geração (NGFW)
Combinam as funções de um firewall tradicional com outras funcionalidades, como inspeção profunda de pacotes (DPI) e sistemas de prevenção de intrusão (IPS).

### 4. WAF (Web Application Firewall)
Protege especificamente aplicações web, filtrando e monitorando o tráfego HTTP entre uma aplicação web e a Internet.

## Regras de Firewall (ACLs)
As regras geralmente seguem a lógica:
`Ação (Permitir/Bloquear) - Protocolo - Origem (IP/Porta) - Destino (IP/Porta)`

## Melhores Práticas
- **Política de Bloqueio Padrão (Default Deny)**: Bloquear tudo por padrão e permitir apenas o necessário.
- **Princípio do Menor Privilégio**.
- **Auditoria Regular de Regras**.
- **Logging**: Manter registros de tráfego bloqueado para análise.