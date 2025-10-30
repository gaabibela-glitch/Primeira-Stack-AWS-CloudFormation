# Primeira-Stack-AWS-CloudFormation
STACK AWS
Projeto:Automação e Gerenciamento

Este repositório documenta o aprendizado sobre AWS CloudFormation e a prática de criar e manter stacks na AWS como código.

Primeiro passo, certifique-se de que:

Você tem acesso a uma Conta AWS com um usuário ou perfil IAM que possua permissões para usar Amazon EC2, Amazon S3 e CloudFormation, ou tenha privilégios administrativos.

Existe uma VPC (Virtual Private Cloud) com acesso à internet. Contas novas da AWS normalmente incluem uma VPC padrão.

Principais componentes de um template

Resources: itens a serem criados (EC2, S3, RDS, etc.).

Parameters: valores que o usuário fornece no momento da criação.

Outputs: informações retornadas pela stack após a criação (ex.: IP público, nome do bucket).

Mappings e Conditions: lógica para adaptar o template a regiões, ambientes ou condições específicas.

Passo a passo detalhado — Criando uma stack pelo AWS Management Console

Acesse o console do CloudFormation.

Clique em Create Stack (Criar stack).

Na página Create stack, escolha Build from Infrastructure Composer (ou Build using the Infrastructure Composer) e depois Create in Infrastructure Composer — isso abrirá o Infrastructure Composer no modo do console do CloudFormation.

Para carregar e validar seu template, vá em Modelos. No editor, copie e cole o template em JSON ou YAML.

Após carregar o template, clique em Avançar.

Em Especificar detalhes da tarefa, insira um Nome da stack (sem espaços).

Em Parâmetros, preencha os valores personalizados exigidos pelo template (por exemplo, tipo de instância, CIDR, nomes).

Clique em Avançar duas vezes para chegar à página Revisar e criar. Na página Configurar opções da stack você pode manter as opções padrão neste tutorial.

Revise todas as configurações. Quando tudo estiver correto, clique em Submit (Enviar) para criar a stack.

Provisionando recursos básicos e gerando Outputs

Ao submeter a stack, o CloudFormation provisiona os recursos declarados em Resources.

No final do processo, a seção Outputs do template exibe valores úteis (por exemplo, URL do site hospedado no S3, ID da instância EC2, endpoints). Esses outputs podem ser reutilizados por outras stacks ou por scripts de automação.

Monitoramento de stacks e eventos

O console do CloudFormation mostra o status da stack (CREATE_IN_PROGRESS, CREATE_COMPLETE, ROLLBACK_IN_PROGRESS etc.).

Na aba Events você acompanha a sequência de ações realizadas (criação de recursos, possíveis erros e mensagens de rollback).

Use essas informações para depurar falhas: a mensagem de evento normalmente aponta qual recurso falhou e por qual motivo, permitindo correção no template ou nas permissões.

Logs e métricas dos próprios serviços (por exemplo, CloudWatch para EC2/Lambda) também ajudam a diagnosticar problemas que não estejam explícitos apenas no CloudFormation.

Casos de uso práticos

Alguns exemplos de aplicação:

Provisionar uma instância EC2 para um servidor web.

Criar um bucket S3 para hospedar um site estático (HTML, CSS, JS).

Boas práticas rápidas

Mantenha templates pequenos e modulares; use nested stacks quando necessário.

Versione seus templates (git) e revise mudanças antes de aplicar em produção.

Use parâmetros e mappings para parametrizar ambientes (dev/stage/prod).

Teste templates em uma conta ou ambiente isolado antes de rodar em produção.

Configure roles IAM com o princípio do menor privilégio.

Conclusão

O AWS CloudFormation é a peça-chave para transformar infraestrutura em código: traz previsibilidade, repetibilidade e controle para provisionamento de recursos na nuvem. Com templates bem estruturados e monitoramento atento das stacks, é possível automatizar ambientes de forma segura e escalável.

Referências (sugestões)

Documentação oficial da AWS — AWS CloudFormation

Artigos e vídeos introdutórios sobre Infrastructure as Code
