# AuRoRA Platform

**AuRoRA — Autonomous Robots for Research and Applications**

Este repositório é a **página de apresentação** da organização
[`AuRoRA-4U`](https://github.com/AuRoRA-4U) e o ponto de partida para quem
deseja utilizar a Plataforma AuRoRA em experimentos, aulas e projetos de
robótica.

A AuRoRA é desenvolvida no  
NERo – Núcleo de Especialização em Robótica, Universidade Federal de Viçosa (UFV).

---

## 1. O que é a AuRoRA?

A AuRoRA não é apenas um robô ou um código isolado.  
Ela é uma **plataforma modular**, composta por vários repositórios, que
organizam:

- **Robôs** (UAVs, UGVs, etc.)  
- **Acessórios e ferramentas** (joysticks, bibliotecas auxiliares…)  
- **Ambientes e mundos** (cenários de simulação, mapas, etc.)  
- **Estratégias e soluções** (controle, planejamento, navegação, etc.)

A ideia é que qualquer pessoa consiga:

- Montar o seu próprio “workspace AuRoRA” na máquina local  
- Escolher quais robôs/sensores/ambientes quer usar  
- Clonar apenas os repositórios necessários  
- Reutilizar a infraestrutura em diferentes experimentos

---

## 2. Estrutura de pastas do ambiente AuRoRA

No seu computador, a recomendação é manter uma pasta principal chamada
**`AuRoRA`**, contendo a seguinte organização:

```text
AuRoRA/
├── !Robots/
├── (Accessories and Tools)/
├── (Environments and Worlds)/
└── (Strategies and Solutions)/
```

Cada subpasta terá os repositórios correspondentes:

* `!Robots/` → repositórios `robot-*` (plataformas robóticas)
* `(Accessories and Tools)/` → repositórios `sensor-*`, `tool-*`
* `(Environments and Worlds)/` → repositórios `world-*`
* `(Strategies and Solutions)/` → estratégias de controle, navegação, etc.

Essa estrutura pode ser criada **automaticamente** pelos scripts
`letsStartAuRoRA` (MATLAB / Python), descritos abaixo.

---

## 3. Preparando o ambiente local

### 3.1. Pré-requisitos

Antes de começar, instale e configure:

1. **Git**

   * Download: [https://git-scm.com/downloads](https://git-scm.com/downloads)
   * Instalação: [https://git-scm.com/book/en/v2/Getting-Started-Installing-Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)

2. **Configuração das credenciais do Git**

   * [Como salvar usuário e senha no Git (StackOverflow)](https://stackoverflow.com/questions/35942754/how-to-save-username-and-password-in-git)
   * [Documentação oficial do git-credential-store](https://git-scm.com/docs/git-credential-store)

3. (Opcional, mas recomendado)

   * **MATLAB** – para usar os scripts em `.m`
   * **Python 3** – para usar o script em `.py`

---

### 3.2. Criando a pasta AuRoRA

1. Escolha um local de fácil acesso no seu computador (por exemplo `C:\Users\SeuUsuario\Desktop\` ou `~/Dev/`).
2. Crie uma pasta chamada **`AuRoRA`** (pode ser via explorador de arquivos ou terminal).

---

### 3.3. Clonando o repositório AuRoRA-Platform

Abra um terminal (cmd, PowerShell, Git Bash, bash, etc.), navegue até a
pasta `AuRoRA` e execute:

```bash
cd /caminho/para/AuRoRA

git clone https://github.com/AuRoRA-4U/AuRoRA-Platform.git
```

Isso criará uma pasta `AuRoRA-Platform` dentro da sua pasta `AuRoRA`:

```text
AuRoRA/
└── AuRoRA-Platform/
    ├── README.md
    ├── setup/
    └── ...
```

---

## 4. Criando automaticamente a estrutura do workspace

Dentro deste repositório existem scripts que criam a estrutura de pastas
mostrada na Seção 2.

### 4.1. Via MATLAB — `letsStartAuRoRA.m`

1. Abra o MATLAB.
2. No MATLAB, navegue até a pasta `AuRoRA-Platform`.
3. Execute:

```matlab
letsStartAuRoRA
```

O script irá:

* Pedir para você escolher uma pasta base

* Criar a pasta `AuRoRA` (caso ainda não exista)

* Criar as subpastas:

  ```text
  !Robots/
  (Accessories and Tools)/
  (Environments and Worlds)/
  (Strategies and Solutions)/
  ```

* Exibir uma mensagem de conclusão.

### 4.2. Via Python — `letsStartAuRoRA.py`

1. Abra um terminal na pasta `AuRoRA-Platform`.
2. Execute:

```bash
python letsStartAuRoRA.py
```

O script em Python:

* Descobre o diretório pai da pasta atual
* Garante a existência das pastas:

  ```text
  !Robots/
  (Accessories and Tools)/
  (Environments and Worlds)/
  (Strategies and Solutions)/
  ```

Depois disso, sua estrutura local estará pronta para receber os repositórios
dos robôs, sensores, ferramentas e ambientes.

---

## 5. Clonando os repositórios da AuRoRA

Com a estrutura de pastas criada, o fluxo típico é:

1. Entrar na pasta correspondente
2. Clonar o repositório desejado da organização `AuRoRA-4U`

Exemplos:

### 5.1. Clonar um robô

```bash
cd /caminho/para/AuRoRA/'!Robots'

git clone https://github.com/AuRoRA-4U/robot-bebop.git
git clone https://github.com/AuRoRA-4U/robot-ardrone.git
```

### 5.2. Clonar ferramentas e sensores

```bash
cd "/caminho/para/AuRoRA/(Accessories and Tools)"

git clone https://github.com/AuRoRA-4U/tool-optitrack.git
git clone https://github.com/AuRoRA-4U/sensor-sick-lms111.git
```

### 5.3. Clonar ambientes e mundos

```bash
cd "/caminho/para/AuRoRA/(Environments and Worlds)"

git clone https://github.com/AuRoRA-4U/world-powerlines.git
git clone https://github.com/AuRoRA-4U/world-seawaves.git
```

(Os nomes dos repositórios são ilustrativos; consulte a página da organização
para a lista atualizada.)

---

## 6. Ferramentas extras de Git em MATLAB

Este repositório também inclui funções MATLAB para facilitar o uso do Git
dentro do próprio ambiente MATLAB.

### 6.1. `AuRoRAgitEnviar`

```matlab
AuRoRAgitEnviar
```

Fluxo:

1. Abre uma janela para você escolher a pasta do repositório (`uigetdir`).
2. Executa `git add .` na pasta escolhida.
3. Pede um texto de resumo das alterações.
4. Executa `git commit -m "<mensagem>"`.
5. Executa `git push -u`.

Serve como um atalho para o ciclo:

```bash
git add .
git commit -m "mensagem"
git push
```

### 6.2. `criarRepositorio(link)`

```matlab
criarRepositorio('https://github.com/AuRoRA-4U/novo-repositorio.git')
```

Fluxo:

1. Executa `git init` na pasta atual.
2. Adiciona o remote: `git remote add origin <link>`.
3. Executa `git add .`.
4. Faz o primeiro commit: `git commit -m "initial commit"`.
5. Dá o push inicial: `git push origin master`.

⚠️ Recomenda-se hoje usar a branch `main` (em vez de `master`), mas o
comportamento pode ser mantido por compatibilidade histórica.

---

## 7. Aprendendo mais sobre Git

Se você está começando no Git, seguem algumas referências recomendadas:

* [Lista de comandos úteis do Git – leocomelli](https://gist.github.com/leocomelli/2545add34e4fec21ec16)
* [Curso em Vídeo – Git e GitHub](https://www.youtube.com/watch?v=xEKo29OWILE&list=PLHz_AreHm4dm7ZULPAmadvNhH6vk9oNZA)
* [Curso Git/GitHub – Prof. José de Assis](https://www.youtube.com/watch?v=FF1f4bKYhoo&list=PLbEOwbQR9lqzK14I7OOeREEIE4k6rjgIj)
* [Awesome git tutorials – jaseemabid](https://gist.github.com/jaseemabid/1321592/c92cffcc522e11b152969108669775c0e700a8e9)
* [treinamento-git – PauloGoncalvesBH](https://github.com/PauloGoncalvesBH/treinamento-git)
* [Tutorial de Git e GitHub para iniciantes – Terminal Root](https://terminalroot.com.br/git/)
* [Artigo sobre Git workflow](https://www.zup.com.br/blog/git-workflow)

---

## 8. Sobre o desenvolvimento da AuRoRA

A AuRoRA é um esforço coletivo de alunos de graduação, pós-graduação e
pesquisadores do NERo/UFV.

No espírito do projeto original:

> GL;HF! 😉
> (Good Luck; Have Fun!)

Se desejar contribuir com a plataforma (melhorias, novos robôs, sensores,
mundos, estratégias), entre em contato com o laboratório ou abra uma Issue
nos repositórios correspondentes.
