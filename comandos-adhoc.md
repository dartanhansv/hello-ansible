# Ansible Iniciante - Comandos Ad-hoc


O comando adhoc é uma eficiente ferramenta de automatização e provavelmente a forma mais intuitiva de começar a estudar o Ansible. Sem ele, a opção seria utilizar os playbooks, desenvolvidos em YAML, o que poderia ser uma barreira para muitos iniciantes.

É extremamente simples executar tarefas básicas em múltiplos hosts remotos utilizando os comandos Adhoc. Vejamos alguns exemplos.






## Exemplos
ansible R1 -m ios_command -a "commands='show ip route'"

ansible R1 -m ios_command -a "commands='show ip interface brief'"


