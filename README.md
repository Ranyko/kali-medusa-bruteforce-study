# Simulação de Ataques de Força Bruta com Kali Linux e Medusa

Projeto desenvolvido como parte do desafio **Criando um Ataque Brute Force de Senhas com Medusa e Kali Linux**, da [DIO](https://www.dio.me/).

## Sobre o projeto

O objetivo deste estudo é compreender o funcionamento de ataques de força bruta contra mecanismos de autenticação, utilizando o Kali Linux e a ferramenta Medusa como referências práticas.

Além de explorar os métodos utilizados, o projeto aborda as vulnerabilidades que permitem esses ataques e as medidas que podem ser adotadas para reduzir seus riscos.

## Tecnologias e ferramentas

- **Kali Linux:** distribuição Linux voltada para testes de segurança.
- **Medusa:** ferramenta que automatiza tentativas de autenticação em diferentes serviços.
- **Metasploitable 2:** máquina virtual propositalmente vulnerável, utilizada em laboratórios.
- **DVWA:** aplicação web desenvolvida para o estudo de vulnerabilidades.
- **VirtualBox:** software de virtualização para criação de ambientes isolados.

## Conceitos estudados

### Ataques de força bruta

Um ataque de força bruta consiste em realizar múltiplas tentativas de autenticação até encontrar uma combinação válida de credenciais.

A eficiência do ataque depende de fatores como a complexidade das senhas, a quantidade de combinações testadas e os mecanismos de proteção implementados no sistema.

### Ataque de dicionário

Diferentemente da força bruta exaustiva, o ataque de dicionário utiliza uma lista predefinida de possíveis senhas, conhecida como *wordlist*.

Essa abordagem explora principalmente o uso de senhas comuns, previsíveis ou reutilizadas.

### Password spraying

O password spraying consiste em testar uma pequena quantidade de senhas comuns contra diferentes contas de usuário.

Essa técnica se diferencia dos ataques concentrados em uma única conta e demonstra a importância de mecanismos de detecção que considerem padrões de autenticação em todo o sistema.

## Utilização do Medusa

O Medusa permite automatizar testes de autenticação em diferentes protocolos, incluindo FTP e SMB.

Um exemplo de estrutura de comando para um laboratório isolado é:

```bash
medusa -h 192.168.56.101 -u usuario_teste -P wordlist.txt -M ftp -t 1
```

| Parâmetro | Função |
|---|---|
| `-h` | Endereço do servidor |
| `-u` | Usuário utilizado no teste |
| `-P` | Arquivo contendo as possíveis senhas |
| `-M` | Módulo correspondente ao serviço |
| `-t` | Número de tarefas simultâneas |

*O endereço e as credenciais são ilustrativos e devem ser substituídos pelos dados de um ambiente controlado.*

O aspecto mais importante não é memorizar esses parâmetros, mas compreender como a ferramenta interage com o serviço de autenticação e interpreta suas respostas.

## Análise de segurança

Os cenários estudados demonstram que a segurança de uma autenticação não depende exclusivamente da senha escolhida pelo usuário.

Um sistema que permite tentativas ilimitadas de login, por exemplo, pode facilitar ataques automatizados, mesmo quando utiliza mecanismos seguros de armazenamento de senhas.

### Medidas de mitigação

| Vulnerabilidade | Medida recomendada |
|---|---|
| Senhas previsíveis | Política de senhas fortes e bloqueio de senhas conhecidas |
| Tentativas ilimitadas | Rate limiting e atrasos progressivos |
| Comprometimento de senhas | Autenticação multifator (MFA) |
| Falta de visibilidade | Logs, monitoramento e alertas |
| Enumeração de contas | Mensagens de erro genéricas |
| Serviços desnecessários | Desativação e restrição de acesso |

O bloqueio temporário de contas também pode ser utilizado, desde que seja configurado cuidadosamente para não permitir ataques de negação de serviço contra usuários legítimos.

## Reflexão sobre o aprendizado

A principal conclusão deste estudo é que compreender a lógica de uma vulnerabilidade é mais importante do que memorizar os comandos de uma ferramenta.

Embora o Medusa facilite a automação das tentativas de autenticação, seu uso isolado não representa uma análise completa de segurança.

É necessário compreender o protocolo utilizado, identificar o comportamento da aplicação e avaliar os mecanismos de proteção existentes.

O estudo também reforçou a importância de desenvolver aplicações que considerem segurança desde sua implementação, especialmente nos mecanismos de autenticação e gerenciamento de credenciais.

## Escopo e limitações

Este repositório apresenta um estudo técnico sobre ataques de força bruta e suas mitigações. Os comandos fornecidos são exemplos educacionais e não representam, por si só, evidências de testes executados.

Os cenários abordados devem ser reproduzidos exclusivamente em ambientes locais, isolados e devidamente autorizados.

## Referências

- [Kali Linux](https://www.kali.org/)
- [Medusa](http://www.foofus.net/jmk/medusa/medusa.html)
- [DVWA](https://github.com/digininja/DVWA)
- [OWASP — Authentication Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Authentication_Cheat_Sheet.html)
- [Nmap Reference Guide](https://nmap.org/book/)

---

**Desenvolvido por [Raniery](https://github.com/Ranyko) como parte da formação em cibersegurança da DIO.**
