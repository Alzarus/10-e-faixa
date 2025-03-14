# 10 e Faixa - Gestão de Babas de Futebol ⚽🏆

## 📌 Visão Geral
O **10 e Faixa** é um aplicativo para gerenciamento de "babas" (peladas de futebol) em Salvador e outras regiões. Ele permite a organização de partidas, controle de jogadores, sorteio de times equilibrados e registro de estatísticas em tempo real.  

## 📂 Estrutura Detalhada do Banco de Dados (Firestore)

### **Coleção: babas**
```json
{
  "babaId": {
    "nome": "Baba dos Aposentados",
    "tipo": "5x5 / 7x7 / 11x11",
    "horario": "Terça 19h",
    "local": "Praia do Flamengo",
    "cidade": "Salvador",
    "aniversario": "2024-06-15",
    "valor": 50.00,
    "adms": ["userId1", "userId2"],
    "membros": ["userId3", "userId4", "userId5"],
    "partidas": ["partidaId1", "partidaId2"],
    "rodadas": 15,
    "mensalidade": {
      "valor": 20.00,
      "vencimento": "2024-04-01",
      "pagantes": ["userId3", "userId4"]
    },
    "configuracoes": {
      "tempos_regulamentares": 2,
      "duracao_tempo": 15,
      "limite_gols_partida": 2,
      "prioridade_mensalistas": true
    }
  }
}
```

### **Coleção: atletas**
```json
{
  "userId": {
    "nome": "Pedro Batista",
    "apelido": "Pedrão",
    "posicao": "ATA/GOL/DEF",
    "nivel": 4.5,
    "destro_canhoto": "Destro",
    "foto": "URL",
    "data_nascimento": "1995-08-10",
    "babas_participando": ["babaId1", "babaId2"],
    "babas_adm": ["babaId1"],
    "estatisticas": {
      "geral": {
        "gols": 10,
        "assistencias": 5,
        "presencas": 8,
        "avaliacoes": [5, 4, 5, 5, 4],
        "defesas_dificeis": 2,
        "furadas": 3,
        "cartoes": {"amarelo": 1, "vermelho": 0},
        "destaques": {
          "pereba": 1,
          "craque": 2,
          "maestro": 1,
          "muralha": 0,
          "bola_murcha": 1
        }
      },
      "babaId1": {
        "gols": 5,
        "assistencias": 3,
        "presencas": 4,
        "avaliacoes": [5, 4, 5],
        "defesas_dificeis": 1,
        "furadas": 1,
        "cartoes": {"amarelo": 0, "vermelho": 0},
        "destaques": {
          "pereba": 0,
          "craque": 1,
          "maestro": 1,
          "muralha": 0,
          "bola_murcha": 0
        }
      }
    },
    "pagamentos": {
      "babaId1": {"status": "pago", "data": "2024-03-10"},
      "babaId2": {"status": "pendente", "data": "2024-03-15"}
    }
  }
}
```

### **Coleção: partidas**
```json
{
  "partidaId": {
    "babaId": "babaId1",
    "data": "2024-03-20",
    "horario_inicio": "19:15",
    "horario_fim": "19:45",
    "times": {
      "time1": ["userId3", "userId4"],
      "time2": ["userId5", "userId6"]
    },
    "placar": {"time1": 2, "time2": 3},
    "gols": [
      {"jogador": "userId3", "assistencia": "userId4", "time": "time1"},
      {"jogador": "userId5", "assistencia": null, "time": "time2"}
    ],
    "cartoes": [
      {"jogador": "userId5", "tipo": "amarelo", "motivo": "Falta dura"},
      {"jogador": "userId6", "tipo": "vermelho", "motivo": "Reclamação excessiva"}
    ],
    "substituicoes": [
      {"saiu": "userId3", "entrou": "userId7", "time": "time1"}
    ],
    "furadas": [
      {"jogador": "userId6", "descricao": "Errou chute na cara do gol"}
    ],
    "defesas_dificeis": [
      {"goleiro": "userId8", "descricao": "Defendeu chute forte no ângulo"}
    ],
    "estatisticas_rodada": {
      "pereba": "userId6",
      "craque": "userId5",
      "maestro": "userId4",
      "muralha": "userId8",
      "bola_murcha": "userId6",
      "artilheiro": "userId5"
    }
  }
}
```

## 📢 Observações
Este modelo detalhado inclui todas as informações e propriedades que podem ser armazenadas no banco de dados Firestore para garantir um funcionamento completo do aplicativo. Ele foi estruturado para manter escalabilidade e facilitar o acesso a estatísticas e regras de negócio dentro do *10 e Faixa*.

## 📅 Roadmap Inicial

### **Fase 1 - Setup Inicial** *(1 semana)*  
- [x] Criar repositório no GitHub  
- [x] Escolher tecnologia (React Native + Expo)  
- [x] Configurar Firebase Firestore e Firebase Auth  
- [ ] Criar estrutura inicial do app  

### **Fase 2 - Cadastro de Atletas** *(2 semanas)*  
- [ ] Criar tela de autenticação (Google Sign-In, email/senha)  
- [ ] Criar tela de cadastro do atleta  
- [ ] Implementar armazenamento de imagens no Firebase Storage  
- [ ] Criar banco de dados de atletas no Firestore  

### **Fase 3 - Cadastro e Gerenciamento de Babas** *(2 a 3 semanas)*  
- [ ] Criar sistema de criação de babas  
- [ ] Criar sistema de busca e associação a babas  
- [ ] Criar sistema de administração de babas  

### **Fase 4 - Gestão das Partidas** *(3 a 4 semanas)*  
- [ ] Criar sorteio equilibrado de times  
- [ ] Criar cronômetro e placar  
- [ ] Criar sistema de registro de gols, assistências e cartões  
- [ ] Criar sistema de substituição de jogadores  
- [ ] Criar sistema de estatísticas e rankings  
- [ ] Criar sistema de avaliação de jogadores  

## 📌 Status do Projeto  
🚀 **Em desenvolvimento (Alpha)**  

