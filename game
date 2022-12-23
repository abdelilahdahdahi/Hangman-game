#include <iostream>
#include <string.h>
using namespace std;
const int NUM_MAX_CARATTERI=21;
const int NUM_MAX_ERRORI=8;
char parola[NUM_MAX_CARATTERI+1];// mettiamo una posizione in più per \0
char suggerimento[NUM_MAX_CARATTERI+1];// mettiamo una posizione in più per \0

const char* corpoImpiccato[]={
  " |\n",
  " O\n",
  "/",
  "|",
  "\\\n",
  " |\n",
  "/",
  " \\\n"
};

/*costruiamo il suggerimento da mostrare al giocatore
all'inizio devo mettere tanti _ quante sono le lettere della parola misteriosa*/
void creaSuggerimento(){
  for(int pos=0; pos < strlen(parola); pos++){
    suggerimento[pos]='_';
  }
  suggerimento[strlen(parola)]='\0';
}
/*nascondi deve scrollare il testo per nascondere la parola inserita*/
void nascondi(){
  for(int conta=100; conta > 0; conta--){
    cout << endl;
  }
}
/* il primo giocatore deve inserire la parola che il secondo giocatore deve indovinare*/
void scegliLaParolaDaIndovinare(){
  cout << "inserisci la parola da indovinare: ";
  cin >> parola;
  nascondi();
  creaSuggerimento();
}
/* controlla se il giocatore ha indovinato TUTTE le lettere della parola segreta*/
void controllaVittoria(){
  bool finito=false;
  for(int pos=0; pos < strlen(suggerimento); pos++){
    if(suggerimento[pos]=='_'){
      return;
    }
  }
  cout << "Hai indovinato la parola segreta: " << suggerimento << " ed hai vinto!" <<endl;
  exit(0);
}
/* devo leggere una lettera e controllare se è presente nella parola*/
bool giocaUnaVolta(){
  cout << "suggerimento: " << suggerimento << endl;
  char lettera;
  cout << "inserisci una lettera: ";
  cin >> lettera;
  bool trovata=false;
  for(int pos=0; pos < strlen(parola); pos++){
    // controllo la lettera
    if(lettera==parola[pos]){
      trovata=true;
      suggerimento[pos]=lettera;
    }
  }
  if(trovata){
    controllaVittoria();
  }

return trovata;  
}
/* devo leggere più lettere e controllare se sono presenti nella parola fino a quando:
a) indovina l'intera parola
b) si compone il corpo dell'impiccato*/
void gioca(){
  int numErrori=0;
  while(numErrori < NUM_MAX_ERRORI){
    if(giocaUnaVolta()){
      cout << "ok"<<endl;
    } else{
      for(int k=0; k <= numErrori;k++){
        cout << corpoImpiccato[k];
      }
      cout << endl;
      numErrori++;
    }
  }
  cout << "Non hai indovinato la parola segreta: " << parola << " ed hai perso!" << endl;
}
int main() {
  scegliLaParolaDaIndovinare();// camel case
  gioca();
}
