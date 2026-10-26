# 🧮 Treinar Tabuada Adaptativa

Aplicativo interativo desenvolvido em Flutter para auxiliar alunos do ensino fundamental no aprendizado da tabuada de multiplicação de forma dinâmica e inclusiva. O sistema implementa uma interface gamer ("arcade") combinada com um algoritmo adaptativo que calibra a dificuldade das questões em tempo real para otimizar a experiência pedagógica.

## 🚀 Diferenciais Técnicos e Regras de Negócio

### 1. Dificuldade Adaptativa e Controle de Tempo
O núcleo lógico do software monitora a performance mecânica e cognitiva do estudante:
*   **Performance Positiva:** Cada acerto dentro do tempo disponível diminui o tempo máximo da próxima questão em **1 segundo** (com piso de segurança fixado em **5 segundos**).
*   **Performance Negativa (Gatilho Adaptativo):** Caso o aluno acumule **2 erros consecutivos** (por resposta errada ou estouro de cronômetro), o algoritmo entende a sobrecarga e incrementa **+2 segundos** no temporizador da próxima questão (com teto máximo em **20 segundos**).

### 2. Persistência e Sistema de Ranking Local
*   **Isolamento por Usuário:** Os dados são gravados localmente via `shared_preferences`. A indexação de chaves higieniza as strings do nome usando `.trim().toLowerCase()`, o que evita duplicidade de perfis em variações de caixa de digitação.
*   **Fórmula do Placar:** O ranking classifica os jogadores baseando-se no saldo real de acertos, calculado pela equação matemática:  
    \[\text{Pontuação} = \text{Número de Acertos} - \text{Número de Erros}\]

### 3. Abordagem Pedagógica Inclusiva
*   Se o saldo final de uma rodada encerrada pelo botão **"Finalizar Jogo"** resultar em um valor negativo, a interface intercepta a renderização e altera o texto padrão para uma **mensagem acolhedora e motivacional**, transferindo o foco do erro para o esforço do aluno.

## 🛠️ Tecnologias e Pacotes Utilizados

*   **Framework:** Flutter (Null-Safety)
*   **IDE recomendada:** Android Studio
*   **Gerenciamento de Estado:** `StatefulWidget` com manipulação reativa de frames.
*   **Persistência:** `shared_preferences: ^2.3.5`
*   **Gerenciamento de Fluxos:** `Timer.periodic` para renderização contínua do cronômetro.

## 📁 Estrutura de Arquivos

```text
lib/
└── main.dart  # Código-fonte unificado contendo Interface, Estado e Conexão Local.
```
