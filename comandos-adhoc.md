# Ansible Iniciante - Comandos Ad-hoc


O comando adhoc é uma eficiente ferramenta de automatização e provavelmente a forma mais intuitiva de começar a estudar o Ansible. Sem ele, a opção seria utilizar os playbooks, desenvolvidos em YAML, o que poderia ser uma barreira para muitos iniciantes.

É extremamente simples executar tarefas básicas em múltiplos hosts remotos utilizando os comandos Adhoc. Vejamos alguns exemplos.







## Módulo ping
Neste primeiro exemplo utilizaremos o módulo ping `[-m ping]` do Ansible para testar a conectividade com o host R1:
![pingr1](https://user-images.githubusercontent.com/87205124/125204488-fe354900-e253-11eb-91a3-b674f2bd850c.JPG "módulo ping")





## Módulo ios_command
Agora vamos de fato executar uma tarefa remotamente: Acessar R1 e rodar o comando *"show ip interface brief"*
![ios_command1](https://user-images.githubusercontent.com/87205124/125204518-202ecb80-e254-11eb-88af-3db86e14ce70.JPG "ios_command")  
Sucesso! A saída do comando executado no host remoto é exibida no terminal.


#### Observação:  
Note que o hostname R1 está no inicio do comando neste segundo exemplo e no final do primeiro. Sim, é indiferente!  
Os comanandos abaixo são equivalentes:  
`ansible R1 -m ios_command -a "commands='show ip route'"`  
`ansible -m ios_command -a "commands='show ip route'" R1`




## Sensacional! Mas o que foi automatizado?  
Nada!  
 Utilizar o Ansible para remotamente executar um comando em um host gera até mais trabalho (digitação) que logar no host e executar o comando diretamente nele. Não faz sentido!  

 Mas calma! Foi apenas um exemplo.  
   
   Agora imagine uma tarefa que demande executar o mesmo comando em vários hosts, consultar a rota default de 100 roteadores, por exemplo.  
   Pensou? Sem uma ferramenta de automação seria necessário digitar seu login, sua senha e comando *"show ip route 0.0.0.0"* 100 vezes, enquanto que no Ansible a tarefa seria executada com apenas um comando:


 `ansible all -m ios_command -a "commands='show ip route 0.0.0.0'"`

 Perceba a sintaxe praticamente idêntica ao exemplo anterior, porém com uma sútil diferença: a substituição do hostname *"R1"* por *"all"*. Esse parâmetro indica que o comando ad-hoc será executado em todos os hosts configurados no arquivo de inventário.  
