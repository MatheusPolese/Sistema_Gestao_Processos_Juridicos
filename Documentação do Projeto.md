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