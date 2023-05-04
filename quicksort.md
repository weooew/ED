Particionar o vetor
A[c..m-1] <= A[m] < A[m+1..r]
Escolha qualquer elem no subarray e chame-o de pivô 
Organize: menores ou igual que pivô -> esquerda
          maiores que pivô -> direita
OBS: Por prática mais a direita da subvetor = pivô
Depois de ordenados os 2 subvetores de acordo com o pivô
Ordene todos os numeros na esquerda e direita

<img align= "right" width= "300" height= "500" src= "https://user-images.githubusercontent.com/102996679/236327577-f6195b2a-a226-4369-af19-d93aa7e13358.png">

```

/* Recebe um vetor A[l..r] com l <= r.
* Rearranja os elementos do vetor e devolve
* j em l..r tal que A[l..j-1] <= A[j] < A[j+1.. r].
*/
int partition (int A[] , int c , int f) {
  int n = f-c+1;//3
  int aux[n];
  int pivo = A[f];
  int i = 0;
  int j = n - 1;//2
  
  for(int cont = l ; cont < f; cont++) { //do começo ao final
    if(A[cont] <= pivo ) aux[i++] = A[cont]; //menor para aux
    else aux[j--] = A[cont];  
  }
  aux[i] = pivo ;
  i = 0;
  for(int cont = c ; cont <= f; cont++) A[cont] = aux [i++];
  return j;
  }
//O(n)

void quicksort (int A[] , int c, int f) {
  if (c < f) {
     int j = partition (A , c, f);
     quicksort (A , c , j-1) ;
     quicksort (A , j+1 , f);
  }
}
```

Pior->  O(n²)
T(n) = 2T(n]2) + O(n)
Médio -> O(n logn)

