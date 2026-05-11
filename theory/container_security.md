# Segurança em Containers (Docker)

A tecnologia de containers, como o Docker, revolucionou o desenvolvimento de software, mas também introduziu novos desafios de segurança.

## Isolamento vs. Virtualização
Ao contrário das Máquinas Virtuais (VMs), os containers compartilham o kernel do sistema operacional hospedeiro. Isso os torna mais leves, mas o isolamento é menos robusto do que o fornecido por um hipervisor.

## Riscos Principais
- **Escalação de Privilégios (Container Breakout)**: Quando um processo dentro de um container consegue acessar o sistema operacional hospedeiro.
- **Imagens Vulneráveis**: Uso de imagens base obsoletas ou que contêm malware/vulnerabilidades conhecidas.
- **Segredos Expostos**: Chaves de API ou senhas incluídas diretamente no `Dockerfile` ou nas camadas da imagem.
- **Privileged Containers**: Rodar um container com a flag `--privileged` remove quase todas as proteções de isolamento.

## Melhores Práticas
1. **Não rodar como Root**: Sempre que possível, configure o container para rodar com um usuário não privilegiado.
2. **Scan de Imagens**: Use ferramentas como o **Trivy** ou **Clair** para buscar vulnerabilidades em suas imagens antes do deploy.
3. **Limitar Recursos**: Defina limites de CPU e memória para evitar ataques de Negação de Serviço (DoS) entre containers.
4. **Usar Imagens Oficiais e Minimalistas**: Prefira imagens como o **Alpine Linux**, que possuem uma superfície de ataque muito menor.
5. **Gerenciamento de Segredos**: Use Docker Secrets ou soluções externas (HashiCorp Vault) em vez de variáveis de ambiente para dados sensíveis.