# Snort - Guia de Instalação e Configuração

## 1) Instalação

### Download e Instalação Manual
Você pode baixar e instalar manualmente pelo site oficial:
[Snort Downloads](https://www.snort.org/downloads#snort)

### Instalação via Repositórios
Se estiver usando um sistema baseado em Debian, pode instalar o Snort diretamente pelos repositórios oficiais com o comando:
```bash
sudo apt-get install snort
```

## 2) Durante a Instalação
Durante a instalação, anote o nome da interface de rede que será inspecionada e a rede que deseja monitorar.

Você pode utilizar os seguintes comandos para identificar a interface:
```bash
ifconfig
```
Ou:
```bash
ip addr
```

## 3) Verificando a Versão Instalado
Após a instalação, confirme a versão do Snort com o seguinte comando:
```bash
snort --version
```

## 4) Configuração
O principal arquivo de configuração do Snort está localizado em:
```bash
sudo gedit /etc/snort/snort.conf
```

Edite esse arquivo conforme necessário para definir as regras e parâmetros de monitoramento.

## 5) Baixando Regras Atualizadas
Para manter o Snort atualizado com as regras mais recentes, você pode optar por um dos seguintes métodos:

### Método Automático
Criar um script para baixar e atualizar as regras periodicamente.

### Método Manual
1. Baixe as regras manualmente pelo site oficial: [Snort Downloads](https://www.snort.org/downloads#snort)
2. Extraia os arquivos para o diretório correto:
   ```bash
   sudo tar -xvzf as_novas_regras.tar.gz -C /etc/snort/rules
   ```

## 6) Configurando a Interface de Rede em Modo Promíscuo
Para capturar pacotes corretamente, configure a interface em modo promíscuo com o seguinte comando:
```bash
sudo ip link set sua_interface promisc on
```
Substitua `sua_interface` pelo nome da interface de rede utilizada.

## 7) Rodando o Snort
Para executar o Snort, utilize o seguinte comando:
```bash
sudo snort -d -l /var/log/snort/ -A console -c /etc/snort/snort.conf
```

### Explicação dos Parâmetros:
- `-d` : Mostra os dados da camada de aplicação
- `-l /var/log/snort/` : Define o diretório onde os logs serão armazenados
- `-A console` : Envia alertas diretamente para a tela
- `-c /etc/snort/snort.conf` : Especifica o arquivo de configuração

---

Este guia serve como um ponto de partida para instalação e configuração do Snort. Para mais detalhes e personalizações avançadas, consulte a documentação oficial do Snort.
