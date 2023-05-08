Implemente o algoritmo Mergesort para dividir o vetor em três partes (aproximadamente) de igual tamanho. Cada parte é então ordenada recursivamente e depois é feito o Intercala simultaneamente nas três partes.
```
#include <iostream>
using namespace std;

void intercala(int A[], int c, int t, int f){
  int *aux = new int[f - c + 1];  // Vetor auxiliar
  int c2 = c;
  int t2 = t;
  int t3 = t*2;
  int cont = 0;

  // Intercala os 3 subvetores ordenados
  while (c2 <= t-1 && t2 <= 2*t-1 && t3 <= f) {
    if (A[c2] <= A[t2] && A[c2] <= A[t3])
      aux[cont++] = A[c2++];
    else if(A[t2] <= A[c2] && A[t2] <= A[t3])
      aux[cont++] = A[t2++];
    else
      aux[cont++] = A[t3++];
  }
  // copiar resto:
  while (c2 <= t-1) aux[cont++] = A[c2++];
  while (t2 <= f) aux[cont++] = A[t2++];
  while (t3 <= f) aux[cont++] = A[t3++];

  // Copia vetor ordenado aux para o vetor A
  for(c2 = c; c2 <= f; c2++) A[c2] = aux[c2 - c];

  delete[] aux; // libera memoria alocada
}

void merge_sort3(int vet[], int ini, int fim){
    if (fim - ini == 1){ //case base 2 elementos
        if(vet[ini] > vet[fim]){
            int aux;
            aux = vet[ini];
            vet[ini] = vet[fim];
            vet[fim] = aux;
        }
    }
    else if(ini < fim) {
        int t = (fim-ini+1)/3;
        
        merge_sort3(vet, ini, ini+t-1);
        merge_sort3(vet, ini+t, ini+2*t-1); 
        merge_sort3(vet, ini+2*t, fim); 
        
        if(fim%3 != 0){ //intercalar só se sobrar
            intercala(vet, ini, ini+2*t-1, fim);
        }
    }
}

int main(){
    int n;
    cin >> n;
    int vetor[n];
    for(int i = 0; i < n; i++){
       cin >> vetor[i];
    }
    merge_sort3(vetor, 0, n-1);
    
    for(int i = 0; i < n; i++) cout << vetor[i] << " ";
    return 0;
}
```

