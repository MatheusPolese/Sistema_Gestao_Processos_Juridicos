# Documentação do Projeto — Sistema de Gestão de Processos Jurídicos

|                           |                                                 |
| ------------------------- | ----------------------------------------------- |
| **Projeto / Sistema**     | Sistema de Gestão de Processos Jurídicos (SGPJ) |
| **Cliente / Solicitante** | Escritório de advocacia do IFSul                |
| **Responsável**           | Matheus Polese                                  |
| **Disciplina**            | Análise e Projeto de Sistemas — 2026/2          |
| **Data**                  | 04/11/2026                                      |
| **Versão**                | 1.0                                             |

## 1. Descrição e delimitação do escopo

### 1.1 Cenário

Um escritório de advocacia atende um grande volume de clientes em ações semelhantes e com etapas padronizadas. Depois que o cliente assina o contrato de honorários, o caso passa por uma sequência de etapas internas até a petição inicial ser protocolada no tribunal:

1. **Documentação** — a equipe de documentação entra em contato com o cliente e reúne os documentos necessários para a ação.
2. **Pré-processual** — com a documentação completa, o caso é distribuído a um advogado, que elabora a petição inicial.
3. **Protocolado** — a petição inicial foi protocolada; a partir daí o caso passa a ser acompanhado também pelo setor financeiro, pois a cobrança dos honorários depende do protocolo.
4. **Análise de renúncia / Renunciado** — quando o cliente deixa de responder ou manifesta desistência, o caso é analisado e pode ser encerrado por renúncia.

Hoje essa coordenação é feita em planilhas compartilhadas, com uma aba por etapa. Os casos são movidos manualmente entre abas (ou por automações externas), a prioridade é calculada por fórmulas e os indicadores de produtividade são montados à mão.

### 1.2 Problema

Hoje, o escritório trabalha com diversas planilhas e ferramentas rígidas que dispersam informações em alto volume. O sistema tem como propósito individualizar, melhorar a visualização e garantir o controle de cada processo. Além disso, o sistema de gestão automatizará rotinas repetitivas, organizará, impedirá que prazos sejam perdidos com alertas e quantificará o desempenho do escritório, evidenciando os pontos de melhoria.

### 1.3 Propósito

O SGPJ centraliza o ciclo de vida do caso, do contrato assinado até o protocolo da petição inicial ou a renúncia, em um sistema web multiusuário. Ele oferece fluxo de status controlado, distribuição de trabalho entre os advogados, priorização automática, histórico completo de cada caso e indicadores de produtividade.

### 1.4 Público-alvo (atores)

| Ator                           | Descrição                                                                                                              |
| ------------------------------ | ---------------------------------------------------------------------------------------------------------------------- |
| **Coordenador**                | Acompanha a operação, distribui os casos entre os advogados, decide as análises de renúncia e consulta os indicadores. |
| **Advogado**                   | Elabora e protocola as petições iniciais dos casos atribuídos a ele.                                                   |
| **Assistente de Documentação** | Cadastra clientes e casos, faz o contato com o cliente e controla o recebimento dos documentos.                        |
| **Financeiro**                 | Registra e acompanha a situação do pagamento dos honorários dos casos protocolados.                                    |
| **Administrador**              | Gerencia usuários, perfis de acesso e parâmetros do sistema.                                                           |

### 1.5 Funcionalidades contempladas

- Cadastro de clientes e de casos (contratos), com honorários e dados da ação.
- Controle da etapa de documentação: registro de contatos e checklist de documentos.
- Cálculo automático da pontuação e da classe de prioridade de cada caso.
- Distribuição de casos aos advogados e fila de trabalho individual.
- Controle do fluxo de status do caso, com histórico.
- Fluxo de análise de renúncia.
- Registro da situação de pagamento dos honorários.
- Painel de indicadores por etapa, relatório de produtividade por advogado e tempos médios entre etapas.

### 1.6 Fora do escopo

- Captação de clientes e atendimento comercial.
- Gestão financeira completa (emissão de boletos, conciliação bancária, fluxo de caixa): o sistema apenas registra a situação do pagamento.
- Integração com plataformas de assinatura eletrônica: o cadastro do contrato é manual.
- Integração com sistemas de tribunais e acompanhamento do processo após o protocolo.

### 2 Fase de análise


### 2.1 Requisitos Funcionais
# Requisitos Funcionais

| ID | Descrição | Prioridade | Depende de |
| --- | --- | --- | --- |
| RF 001 | O sistema deve permitir a autenticação por e-mail e senha e liberar a cada perfil apenas as suas funções: o Administrador gerencia usuários e parâmetros da operação (documentos obrigatórios, formas de pagamento e feriados); o Coordenador distribui casos e acompanha painel e relatórios; o Advogado trabalha os seus casos e protocola petições; o Assistente de Documentação cadastra clientes e casos, controla contatos e documentos; o Financeiro controla os pagamentos. | Alta | — |
| RF 002 | O sistema deve permitir cadastrar clientes (nome, CPF, telefone, e-mail e UF) e casos vinculados a eles (data de assinatura do contrato, valor da causa, honorários, forma de pagamento, descrição da ação, prioridade e indicação de réu federal). O caso é criado na etapa Documentação e pode assumir as situações Pré-processual, Protocolado e Renunciado. | Alta | RF 001 |
| RF 003 | O sistema deve permitir registrar as tentativas de contato com o cliente (data, meio e observação) e controlar o checklist de documentos obrigatórios do caso, registrando a data de recebimento de cada documento. | Alta | RF 002 |
| RF 004 | O sistema deve permitir encaminhar o caso da etapa Documentação para a etapa Pré-processual e permitir que o coordenador distribua e redistribua o caso a um advogado, definindo a data prevista de entrega da petição inicial. | Alta | RF 003 |
| RF 005 | O sistema deve exibir ao advogado a sua fila de casos, ordenada pela data prevista de entrega, e permitir que ele atualize a situação da petição inicial (Em andamento, Em correção, Protocolada), exigindo a data do protocolo ao protocolar e movendo o caso para a etapa Protocolado. | Alta | RF 004 |
| RF 006 | O sistema deve permitir que o financeiro registre e atualize a situação do pagamento dos honorários (Pendente, Pago, Atrasado, Êxito) dos casos protocolados, tendo a data do protocolo como base para o controle dos prazos. | Média | RF 005 |
| RF 007 | O sistema deve manter o histórico de cada caso, gravando automaticamente mudanças de etapa, situação e responsável (data, hora e usuário), permitir anotações livres e permitir pesquisar e filtrar casos por cliente, etapa, situação, advogado, pagamento e período. | Alta | RF 002 |
| RF 008 | O sistema deve apresentar ao coordenador um painel por etapa e situação (quantidade, percentual, soma de honorários e valores de causa, filtrável por mês) e gerar relatórios de produtividade dos advogados e de tempos médios entre as etapas em um período informado. | Média | RF 005 |
| RF 009 | O sistema deve se integrar aos tribunais para acompanhar os processos dos casos protocolados e identificar novidades. | Média | RF 005 |
| RF 010 | O sistema deve se integrar aos meios de contato do escritório e avisar o cliente por e-mail ou WhatsApp quando houver novidades no processo ou documentos pendentes. | Média | RF 003, RF 009 |
