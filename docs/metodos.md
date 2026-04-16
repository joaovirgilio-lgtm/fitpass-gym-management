@startuml

class Aluno {
  - id: int
  - nome: String
  - cpf: String
  - email: String
  - telefone: String
  - endereco: String
  - status: String
  + realizarPagamento()
  + agendarAula()
}

class Plano {
  - id: int
  - nome: String
  - tipo: String
  - valor: double
  - duracaoDias: int
  - ativo: boolean
  + ativar()
  + desativar()
}

class Pagamento {
  - id: int
  - data: Date
  - valor: double
  - status: String
  - metodo: String
  + registrarPagamento()
}

class Acesso {
  - id: int
  - dataHoraEntrada: DateTime
  - dataHoraSaida: DateTime
  + registrarEntrada()
  + registrarSaida()
}

class Aula {
  - id: int
  - nome: String
  - horario: DateTime
  - capacidadeMaxima: int
  + adicionarAluno()
  + removerAluno()
}

class Agendamento {
  - id: int
  - data: Date
  - status: String
  + confirmar()
  + cancelar()
}

class Presenca {
  - id: int
  - data: Date
  - presente: boolean
  + registrarPresenca()
}

class AvaliacaoFisica {
  - id: int
  - data: Date
  - peso: double
  - altura: double
  - observacoes: String
  + registrarAvaliacao()
}

class Notificacao {
  - id: int
  - mensagem: String
  - dataEnvio: Date
  - lida: boolean
  + enviar()
}

abstract class Funcionario {
  - id: int
  - nome: String
  - email: String
  - salario: double
}

class Instrutor {
  - especialidade: String
  + ministrarAula()
}

class Recepcionista {
  + cadastrarAluno()
  + registrarPagamento()
}

class Gerente {
  + gerarRelatorios()
  + gerenciarPlanos()
}

' ================= RELACIONAMENTOS =================

Aluno "1" -- "1" Plano : possui
Aluno "1" -- "*" Pagamento : realiza
Aluno "1" -- "*" Acesso : registra
Aluno "1" -- "*" Agendamento : faz
Aluno "1" -- "*" AvaliacaoFisica : possui
Aluno "1" -- "*" Notificacao : recebe

Aula "1" -- "*" Agendamento : possui
Agendamento "*" -- "1" Aula
Agendamento "*" -- "1" Aluno

Presenca "*" -- "1" Aula
Presenca "*" -- "1" Aluno

Instrutor "1" -- "*" Aula : ministra

Funcionario <|-- Instrutor
Funcionario <|-- Recepcionista
Funcionario <|-- Gerente

@enduml
