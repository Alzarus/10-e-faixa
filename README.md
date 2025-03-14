# 10 e Faixa - Gestão de Babas de Futebol ⚽🏆

## 📌 Visão Geral
O **10 e Faixa** é um aplicativo para gerenciamento de "babas" (peladas de futebol) em Salvador e outras regiões. Ele permite a organização de partidas, controle de jogadores, sorteio de times equilibrados e registro de estatísticas em tempo real.  

## 🚀 Funcionalidades Principais

✅ **Cadastro de atletas** com nome, posição, nível, data de nascimento e foto  

✅ **Criação e administração de babas**, permitindo busca e associação de jogadores  

✅ **Registro do aniversário do baba**, com notificações para os jogadores  

✅ **Controle de rodadas e partidas**, com cronômetro e placar em tempo real, além do registro de ocorrências da partida (gols, assistências, cartões, defesas difíceis, furadas/paçocadas e substituições)  

✅ **Sorteio automático de times equilibrados**, considerando o nível dos jogadores:  
   - O **time vencedor** permanece na quadra.  
   - O **time perdedor sai** e um novo time entra no jogo.
   - Em **caso de empate** o app faz um sorteio para ver quem fica e quem sai.  
   - Se não houver jogadores suficientes para três times, o time perdedor será **sorteado** e um jogador **ficará de fora** temporariamente.  
   - **Evita que convidados caiam no mesmo time**.  
   - **Prioridade para jogadores mensalistas do baba**.  
   - **Distribuição considerando classificação do atleta**, equilibrando os times.  

✅ **Registro detalhado da partida**, incluindo gols, assistências, cartões e substituições  

✅ **Registro de estatísticas individuais e coletivas**, com rankings semanais, mensais e anuais  

✅ **Sistema de avaliação pós-jogo**, onde jogadores avaliam uns aos outros de 0 a 5 estrelas  

✅ **Destaques da rodada** (calculados automaticamente após cada rodada):  
   - 🏆 **Pereba**: Jogador com a **pior média de avaliações** da rodada.  
   - ⚽ **Artilheiro**: Jogador com **mais gols marcados** na rodada.  
   - 🥅 **Muralha**: Goleiro com **mais defesas difíceis** registradas na rodada.
   - 🎩 **Maestro**: Jogador com **mais assistências** na rodada.  
   - ⭐ **Craque**: Jogador com **melhor média de avaliações** na rodada.  
   - 😵 **Bola Murcha**: Jogador com **mais registros de furadas/paçocadas** na rodada.  

✅ **Histórico de conquistas dos jogadores**, contabilizando quantas vezes foram destaque em cada categoria  

✅ **Diferenciação entre jogadores diaristas e mensalistas** dentro do baba  

✅ **Gerenciamento financeiro**, permitindo o registro de mensalidades e pagamentos pelos administradores  

✅ **Notificações de aniversário** dos jogadores para incentivar interações no baba  

## 🏗️ Tecnologias Utilizadas

- **Frontend:** React Native + Expo  
- **Banco de Dados:** Firebase Firestore  
- **Autenticação:** Firebase Auth  
- **Armazenamento de Imagens:** Firebase Storage  
- **Hospedagem:** Firebase Hosting (se necessário para backend futuramente)  

## 📂 Estrutura do Banco de Dados (Firestore)

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
    "rodadas": 15
  }
}
```

### **Coleção: atletas**
```json
{
  "userId": {
    "nome": "Pedro Batista",
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
        "destaques": { "pereba": 1, "craque": 2, "maestro": 1 }
      },
      "babaId1": { 
        "gols": 5, 
        "assistencias": 3, 
        "presencas": 4, 
        "avaliacoes": [5, 4, 5],
        "defesas_dificeis": 1,
        "furadas": 1,
        "destaques": { "pereba": 0, "craque": 1, "maestro": 1 }
      }
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
    "times": {
      "time1": ["userId3", "userId4"],
      "time2": ["userId5", "userId6"]
    },
    "placar": { "time1": 2, "time2": 3 },
    "gols": [{ "jogador": "userId3", "assistencia": "userId4" }],
    "cartoes": [{ "jogador": "userId5", "tipo": "amarelo" }],
    "substituicoes": [{ "saiu": "userId3", "entrou": "userId7" }],
    "furadas": [{ "jogador": "userId6", "descricao": "Errou chute na cara do gol" }],
    "defesas_dificeis": [{ "goleiro": "userId8", "descricao": "Defendeu chute forte no ângulo" }]
  }
}
```

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

## 📢 Contribuição  
Se deseja contribuir, clone o repositório e siga as diretrizes de código!  

```bash
git clone https://github.com/seu-usuario/10-e-faixa.git
cd 10-e-faixa
npm install
npm start
```

## 📌 Status do Projeto  
🚀 **Em desenvolvimento (Alpha)**  
