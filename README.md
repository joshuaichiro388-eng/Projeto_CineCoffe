# CineCoffe
<img width="489" height="357" alt="image" src="https://github.com/user-attachments/assets/ff1b1406-4a12-4182-b8c3-5dc3d6b88d36" />

## Objetivo
Sistema desktop desenvolvido em Java com interface gráfica Java Swing para o gerenciamento completo das operações de um cinema, permitindo administrar filmes, salas, sessões, clientes e funcionários. O sistema também possibilita controlar fluxos operacionais como a compra e a venda de ingressos, aplicando regras de negócio robustas, além de consultar e organizar as informações por meio de filtros dinâmicos e ordenações baseadas em programação funcional.

## Domínio Escolhido
Cinema

## Integrantes
- Gabriel Pereira Jorge
- Joshua Ichiro Taniguchi

## Principais Funcionalidades
- **Gerenciamento de Cadastros**: Telas completas para cadastro, alteração, remoção e listagem de Filmes, Salas, Sessões, Clientes e Funcionários.
- **Fluxo de Alteração Dinâmica**: Seleção de registros na tabela da interface, carregamento automático para os campos do formulário para edição e salvamento.
- **Compra de Ingressos**: Permite ao cliente adquirir entradas (inteira ou meia-entrada), calculando o valor automaticamente e realizando a reserva e ocupação da vaga na sessão correspondente.
- **Venda e Faturamento**: Permite ao funcionário registrar a efetivação da venda de um ingresso previamente comprado, registrando quem realizou a venda e a data/hora da operação.
- **Consultas Avançadas**: Módulos dedicados à consulta de sessões e ingressos com múltiplos critérios de filtros simultâneos, ordenações customizadas e cartões de resumo estatístico em tempo real.

## Lista das Entidades
- **Pessoa (Abstrata)**: Classe base contendo nome, CPF, data de nascimento e telefone.
- **Cliente (Herdeira)**: Herda de Pessoa e acrescenta o atributo e-mail.
- **Funcionario (Herdeira)**: Herda de Pessoa e acrescenta cargo e salário.
- **Filme**: Contém título, gênero, classificação indicativa, duração e nota.
- **Sala**: Contém número, capacidade e tipo (2D ou 3D).
- **Sessao**: Relaciona filme, sala, horário, status e vagas disponíveis.
- **Ingresso (Superclasse)**: Associa sessão, cliente, funcionário vendedor, status, data de compra, data de venda e preço final.
- **IngressoInteira**: Subclasse de Ingresso que calcula o valor com base no preço cheio.
- **IngressoMeia**: Subclasse de Ingresso que aplica o desconto de 50% sobre o valor da sessão.

## Lista dos Cadastros
- **Filmes**: Inserção, alteração, exclusão e limpeza de campos.
- **Salas**: Inserção, alteração, exclusão e limpeza de campos.
- **Sessões**: Gerenciamento de horários e status dinâmicos (Agendada, Em cartaz, Encerrada ou Cancelada).
- **Clientes**: Cadastro e manutenção de dados de público.
- **Funcionários**: Cadastro e manutenção da equipe com cargos e salários.

## Lista das Consultas
- **Consulta de Sessões**
  - **Filtros**: Gênero do filme, tipo de sala e restrição para exibir somente sessões com vagas disponíveis.
  - **Ordenação**: Por horário ou por nota do filme utilizando Collections e Comparators.
  - **Resumo Estatístico**: Quantidade total de sessões encontradas e somatória de vagas disponíveis.
- **Consulta de Ingressos**
  - **Filtros**: Status do ingresso e cliente associado utilizando composição de Predicates.
  - **Ordenação**: Por data da compra ou por preço final.
  - **Resumo Estatístico**: Quantidade de ingressos listados e faturamento total dos ingressos com pagamento confirmado.

## Lista dos Movimentos
- **Comprar Ingresso**: O cliente seleciona uma sessão e o tipo de ingresso (inteira/meia). O sistema valida a disponibilidade de vagas, calcula o valor correspondente, altera o estoque de vagas da sessão e gera o registro do ingresso com status de reservado.
- **Vender Ingresso**: O funcionário seleciona um ingresso adquirido, valida o operador e confirma o recebimento. O status do ingresso é atualizado para pago, registrando o funcionário responsável e a data da transação financeira.

## Arquitetura e Conceitos Aplicados
O projeto foi estruturado aplicando os principais conceitos de orientação a objetos e programação avançada exigidos pela disciplina:
- **Herança e Classes Abstratas**: Estrutura hierárquica em `Pessoa`, `Cliente`, `Funcionario`, bem como na árvore de `Ingresso`.
- **Sobrecarga e Sobrescrita**: Métodos customizados para formatação de dados e cálculo polimórfico de preços.
- **Interfaces e Generics**: Uso da interface de repositório genérico (`Repositorio<T>`) implementada em memória (`RepositorioEmMemoria<T>`).
- **Programação Funcional**: Aplicação intensiva de Funções Lambda, `Predicate`, composição de predicados e `Function` para mapeamento e transformação de coleções de dados.
- **Separação de Responsabilidades**: Organização rigorosa em pacotes (`model`, `view`, `service`, `repository`, `enums`, `util`), isolando a interface gráfica da regra de negócio.

---

## Demonstração da Interface Gráfica

### Tela Principal e Painéis de Navegação
<img width="1153" height="713" alt="image" src="https://github.com/user-attachments/assets/c14c735a-fff4-4191-aec0-2f1d36b0ad6e" />


### Telas de Cadastro
<img width="1157" height="714" alt="image" src="https://github.com/user-attachments/assets/390b0058-65a6-4281-ad66-883a3cf4cd3e" />
<img width="1159" height="712" alt="image" src="https://github.com/user-attachments/assets/416290b5-fd4e-44c9-89dd-0cb00183a377" />
<img width="1158" height="711" alt="image" src="https://github.com/user-attachments/assets/b7643605-4ad6-42f5-8e68-f2598bb6090d" />
<img width="1154" height="712" alt="image" src="https://github.com/user-attachments/assets/d045549a-df6a-42c2-8f69-851f81fc804b" />
<img width="1162" height="713" alt="image" src="https://github.com/user-attachments/assets/54238f26-2276-4899-b392-333e0a777fb1" />


### Telas de Movimentação (Compra e Venda)
<img width="1159" height="716" alt="image" src="https://github.com/user-attachments/assets/e9ac24ec-6b76-469c-abf3-4f43339cbfeb" />
<img width="1161" height="716" alt="image" src="https://github.com/user-attachments/assets/fc215f27-d779-40b8-8cd7-66f6c650c170" />


### Telas de Consulta e Resumos
<img width="1160" height="717" alt="image" src="https://github.com/user-attachments/assets/4ddba244-0df3-419e-bff9-56a8b7e77152" />
<img width="1157" height="712" alt="image" src="https://github.com/user-attachments/assets/3b9b5ba6-e224-4fba-ad98-0a95203a7d6d" />

---

## Instruções para Execução
1. Certifique-se de possuir o Java Development Kit (JDK) instalado em sua máquina (versão 11 ou superior recomendada).
2. Clone o repositório ou descompacte o projeto em sua máquina.
3. Abra o projeto em sua IDE Java de preferência (como IntelliJ IDEA, Eclipse ou NetBeans).
4. Localize a classe principal de entrada `Main` localizada dentro do pacote `cinema`.
5. Execute a classe `Main` para iniciar a aplicação desktop baseada em Java Swing.
![Demonstração do Sistema](./imagens/tela-principal.gif)

![Java](https://img.shields.io/badge/Java-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white)
![Swing](https://img.shields.io/badge/Java_Swing-007396?style=for-the-badge&logo=java&logoColor=white)

