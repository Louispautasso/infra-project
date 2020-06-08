
# Bienvenue au projet 3 !
Le projet a été fait pour Y-NOV dans le cadre du Bachelor 3 informatique orienté Réseaux. Il a été conçu par SUGAC Mihail et PAUTASSO Louis
	
Ce repository consiste à:

 - Créer 4 VM: 1 Registry, 1 HaProxy et 2 noeuds pour un cluster swam
 - Déployer et gerer des utilisateurs et leurs permissions
 - Installer Docker et Docker swarm dans un Cluster et sur un serveur StandAlone
 - Installer la registry docker pour gerer nos images
 - Installer un HaProxy pour gerer le LoadBalancing entre les noeuds du cluster
 - Installer un outil de supervision de conteneurs et de serveurs

Les machines:
 - Registry: 192.168.99.10 // Debian 10
 - HaProxy: 192.168.99.15 // Debian 10
 - Swarm01 : 192.168.99.21 // Debian 10
 - Swarm02: 192.168.99.22 // Debian 10
	
# Acceder aux ressources annexes du projet
Il faut se rendre dans le répertoire `annexe` , ici on pourra trouver le Cahier des charges ainsi que le diagramme de Gantt et le schéma d'architecture réseaux

	
# Déployer les VM

Il faut tout dabord installer [Vagrant](https://linuxize.com/post/how-to-install-vagrant-on-ubuntu-18-04/) sur  sa machines, puis aller dans le repertoire vagrant 

    cd vagrant && vagrant up

# Lancer le playbook Ansible

Avant toute chose, il faut installer [Ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html#installing-ansible-on-ubuntu) Puis aller dans le repertoire ansible et lancer le playbook.

    cd ansible

    ansible-playbook -i hosts playbook.yml

# Valider les tests

Se connecter à l'interface HaProxy avec les identifiants `admin:admin`

[http://192.168.99.15:1936/](http://192.168.99.15:1936/) 

Se connecter aux noeuds du cluster Swarm sur le port 19999 (Application Netdata)

[http://192.168.99.21:19999/](http://192.168.99.21:19999/)

[http://192.168.99.22:19999/](http://192.168.99.21:19999/)

Se connecter aux noeuds du cluster Swarm par le biais de l'HaProxy

[http://192.168.99.15:19999/](http://192.168.99.15:19999/)
