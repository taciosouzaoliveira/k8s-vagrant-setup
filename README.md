# Ambiente de Cluster com Vagrant e VirtualBox

Este projeto configura um ambiente de aprendizado com um cluster simulado usando `Vagrant` e `VirtualBox`. Ele cria uma máquina master e duas máquinas worker, todas rodando Ubuntu Bionic (18.04), que podem ser usadas para estudar Kubernetes e configurações de infraestrutura de TI em ambientes de cluster.

## Visão Geral do Projeto

O ambiente é composto de três máquinas virtuais:
- **Master-1**: Nó principal, onde o controle do cluster e a orquestração ocorrem.
- **Worker-1 e Worker-2**: Nós de trabalho que podem ser configurados para rodar containers em um ambiente de Kubernetes simulado.

## Pré-requisitos

Para usar este projeto, você precisa ter:
- **Vagrant**: 2.2.x ou superior ([Instalar Vagrant](https://www.vagrantup.com/docs/installation))
- **VirtualBox**: 6.1.x ou superior ([Instalar VirtualBox](https://www.virtualbox.org/wiki/Downloads))

**Nota:** Certifique-se de que o módulo do kernel do VirtualBox (`vboxdrv`) está carregado corretamente antes de rodar o Vagrant.

## Estrutura do Arquivo

O arquivo `Vagrantfile` configura as máquinas virtuais e define:
- **Rede Privada**: IPs estáticos para cada VM, acessíveis apenas localmente.
- **Provisão SSH**: Carregamento de chave SSH pública para acesso seguro a cada máquina.
- **Configuração de Hardware**: Número de CPUs e quantidade de memória RAM para cada VM.

## Como Usar

1. Clone este repositório:
   ```bash
   git clone https://github.com/taciosouzaoliveira/seurepositorio.git
   cd seurepositorio
