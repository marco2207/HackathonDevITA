# HackathonDevITA

# Apertura account Bluemix seguire link sottostante:

        http://ibm.biz/BMcom16

# Creazione di un deployment Kubernetes per i seguenti elementi:

-WordPress

-Drupal

-SPID Test Environment

Per tutti e' necessario avere eseguito:

  -la procedura di login a Bluemix tramite command line 
  
  -avere creato un Cluster in Bluemix Kubernetes (accesso dalla console)
  
I comandi da eseguire per creare i Deployments sono i seguenti (dalla directory in cui si trovano i file .yaml):

  a) Ottenimento info (Nome ed ID del CLuster), salvate questi due valori
  
   --> bx cs clusters
  
  b) Impostazioni variabili di ambiente
  
   --> bx cs cluster-config “Your cluster ID”  (ottenuto dal comando precedente come output)
  
  c) eseguire il comando restituito che inizia con "export", nel mio caso:
  
   --> export KUBECONFIG=/Users/marco/.bluemix/plugins/container-service/clusters/00f707e0cf8a4f558ea47bbc3b83390f/kube-config-par01-Dev-ItalyCluster.yml
  
  d) verificare di ottenere dal comando seguenta la versione del client ma soprattutto del server come riposta :
  
   --> kubectl version --short 
  
  e) per la creazione del deployment drupal (sostituire con il file necessario per creare altri oggetti)
  
   --> kubectl create -f drupal.yaml
  
  f) per ottenere l'indirizzo IP di ascolto del nodo del vostro cluster Kubernetes digitare mettendo il nome del cluster come da punto (a)
  
   --> bx cs workers nome_del_vs_cluster
  
  g) la porta di ascolto del servizio appena configurato la trovate nel file yaml ma se volete questo il comando per ottenerla (nome_del_servizio = drupal in questo caso)
  
   --> kubectl get services nome_del_servizio
  
  h) per verificare che tutto sia stato creato correttamente potete aprire la console Kuebernetes eseguendo:
  
   --> kubectl proxy
  
   --> aprire un browser alla porta http://localhost:8001/ui
  
  i) infine aprendo il browser alla pagina costituita dall'indirizzo IP e la porta ottenuti ai punti (f) e (g) vi apparira' il setup di Drupal. 
  
  La mia istanza sul cluster Kubernetes in Germania e' la seguente:
  
  http://169.51.8.40:30380


Tutti coloro che ne faranno richiesta possono agire in 2 modi:

-metodo 1 preferibile : aprire un account Bluemix e creare con loro quanto serve
-metodo 2 creare un utente sui nostri ambienti e fargli utilizare i nostri cluster
