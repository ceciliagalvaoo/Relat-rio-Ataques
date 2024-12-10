## **Relatório Técnico de Segurança do Projeto**  

### **1. Introdução**  

- **Projeto**: Projeto IoT do Grupo Sense  
- **Descrição**: Este relatório técnico apresenta a análise de segurança do Projeto IoT do Grupo Sense, desenvolvido para monitoramento ambiental em florestas. O foco do relatório é identificar vulnerabilidades no sistema, avaliar possíveis ataques cibernéticos e consolidar as informações em um formato estruturado. Além disso, inclui uma tabela classificando os riscos de ataques, priorizando aqueles com maior impacto e probabilidade de ocorrência.  
- **Objetivo**: Consolidar as análises de segurança do Projeto IoT, destacando as vulnerabilidades encontradas, os potenciais ataques e as medidas de mitigação. Este relatório busca fornecer uma visão detalhada sobre os riscos associados ao projeto, assegurando a confiabilidade e a proteção dos dados coletados pelos dispositivos IoT.  
- **Contexto**: No desenvolvimento de sistemas IoT voltados ao monitoramento ambiental, a segurança é um fator crítico devido à sensibilidade dos dados coletados e à possibilidade de comprometimento por agentes maliciosos. Este relatório foi elaborado para identificar pontos fracos no Projeto IoT do Grupo Sense e oferecer uma avaliação clara sobre os possíveis impactos de ataques cibernéticos, orientando futuras implementações de segurança.  

### **2. Identificação de Vulnerabilidades e Possíveis Ataques**  

#### **2.1. Vulnerabilidades Identificadas**  
- **Vulnerabilidade 1**: Dados não criptografados  
- **Vulnerabilidade 2**: Acesso físico fácil ao ESP32  
- **Vulnerabilidade 3**: Utilização do Ubidots como dashboard  
- **Vulnerabilidade 4**: Utilização da mesma rede para todos os dispositivos  
- **Vulnerabilidade 5**: Falta de autenticação robusta  

#### **2.2. Possíveis Ataques**  

1. **Ataque 1 - Interceptação de Dados (MitM)**  
   - **Descrição**: O invasor pode interceptar os dados em trânsito entre os dispositivos e o servidor, alterando ou visualizando informações sensíveis.  
   - **Consequências**: Comprometimento da integridade e confidencialidade dos dados, exposição de credenciais, e potencial controle indevido dos dispositivos.  
   - **Nível de impacto**: Alto  
   - **Vulnerabilidade Relacionada**: V01  

2. **Ataque 2 - Extração de Código do ESP32 (Engenharia Reversa)**  
   - **Descrição**: Acesso físico ao ESP32 permite a extração do código-fonte para análise e engenharia reversa, expondo segredos e vulnerabilidades do sistema.  
   - **Consequências**: Exposição de credenciais, acesso ao Wi-Fi, replicação não autorizada do dispositivo e sabotagem do sistema.  
   - **Nível de impacto**: Muito Alto  
   - **Vulnerabilidade Relacionada**: V02  

3. **Ataque 3 - Comprometimento da Rede Local**  
   - **Descrição**: Uso da mesma rede para todos os dispositivos facilita o acesso a dispositivos IoT caso a rede seja comprometida.  
   - **Consequências**: Controle total dos dispositivos conectados, interrupção de serviços, e exposição de informações sensíveis.  
   - **Nível de impacto**: Alto  
   - **Vulnerabilidade Relacionada**: V04  

4. **Ataque 4 - Uso Indevido do Dashboard (Ubidots)**  
   - **Descrição**: A falta de restrições no acesso ao dashboard permite que um atacante visualize e manipule os dados coletados.  
   - **Consequências**: Alteração de configurações, manipulação de relatórios, e perda de credibilidade do sistema.  
   - **Nível de impacto**: Médio  
   - **Vulnerabilidade Relacionada**: V03  

### **3. Tabela Consolidada de Riscos**  

| **Título do Ataque**               | **Tipo de Ataque**              | **Nível de Impacto** | **Nível de Risco** | **Vulnerabilidade Relacionada** |  
|------------------------------------|---------------------------------|----------------------|--------------------|---------------------------------|  
| Extração de Código do ESP32        | Engenharia Reversa              | Muito Alto           | Alto               | V02                             |  
| Interceptação de Dados             | MitM (Man in the Middle)        | Alto                 | Alto               | V01                             |  
| Comprometimento da Rede Local      | Ataque à Rede                   | Alto                 | Médio              | V04                             |  
| Uso Indevido do Dashboard          | Manipulação Remota              | Médio                | Médio              | V03                             |  

### **4. Conclusão**  
O relatório identificou cinco principais vulnerabilidades no Projeto IoT do Grupo Sense, destacando dois ataques com alto impacto e risco. As medidas de mitigação recomendadas incluem:  
- **Criptografia de Dados e Comunicação**: Adotar protocolos seguros como HTTPS e TLS/SSL para proteger a transmissão de dados entre o ESP32 e os servidores, além de criptografar informações sensíveis armazenadas. Isso garante a confidencialidade dos dados, dificultando a interceptação e manipulação por terceiros.  
- **Proteção Física do Dispositivo**: Alojar o ESP32 em cases robustos e seguros, reduzindo o risco de acesso físico. Sensores de violação podem ser adicionados para alertar sobre tentativas de manipulação, garantindo a proteção do hardware contra ataques diretos.  
- **Segmentação de Rede**: Isolar dispositivos IoT em uma rede separada, utilizando VLANs ou redes Wi-Fi dedicadas. Essa medida reduz os danos de um ataque, limitando sua propagação para outros sistemas ou dispositivos conectados.  
- **Autenticação Segura e Controle de Acesso**: Implementar autenticação multifator e senhas fortes para acesso ao sistema e ao dashboard. Além disso, gerenciar permissões com rigor, garantindo que apenas usuários autorizados possam realizar alterações ou acessar informações sensíveis.   

### **5. Referências**  
- CABRAL, Nicholas Fialho; SILVA, Thiago Gomes. Teste de penetração: utilização da metodologia Owasp em aplicações web.
- DE OLIVEIRA, Nairobi Spiecker et al. Segurança da informaçao para internet das coisas (iot): uma abordagem sobre a lei geral de proteçao de dados (lgpd). Revista Eletrônica de Iniciação Científica em Computação, v. 17, n. 4, 2019.
- ROSA, João Pedro Gomes. Mecanismos de Segurança IoT. Universidade de Nova Lisboa, Portugal, 2021.
- SAMPAIO, Felipe Ferreira. Uma análise prática das principais vulnerabilidades em aplicações web baseado no top 10 OWASP. 2021.
- WICHERS, Dave; WILLIAMS, Jeff. Owasp top-10 2017. OWASP Foundation, v. 3, p. 4, 2017.

### **6. Contribuição Individual**  

- **Cecília Beatriz Melo Galvão**: Compartilhamento de ideias e criação do relatório.  
- **Davi de Oliveira Ferreira**: Identificação dos tipos de ataque.  
- **Davi Nascimento de Jesus**: Descrição do Ataque 1 e Ataque 2 e avaliação do nível de impacto.  
- **Kauã Rodrigues dos Santos**: Nenhuma contribuição registrada.  
- **Lucas Cozzolino Tort**: Compartilhamento de ideias sobre vulnerabilidades.  
- **Matheus Fernandes Guimarães de Sousa**: Compartilhamento de ideias sobre vulnerabilidades.  
- **Vinicius Maciel Flor**: Nenhuma contribuição registrada.  
- **Yasmim Marly Passos**: Identificação das vulnerabilidades e ataques.  
