Particionar o vetor
A[c..m-1] <= A[m] < A[m+1..r]
Escolha qualquer elem no subarray e chame-o de pivô 
Organize: menores ou igual que pivô -> esquerda
          maiores que pivô -> direita
OBS: Por prática mais a direita da subvetor = pivô
Depois de ordenados os 2 subvetores de acordo com o pivô
Ordene todos os numeros na esquerda e direita


´´´cpp
/* Recebe um vetor A[l..r] com l <= r.
* Rearranja os elementos do vetor e devolve
* j em l..r tal que A[l..j-1] <= A[j] < A[j+1.. r].
*/
int partition ( int A [] , int l , int r) {
  int n = r-l+1;
  int aux[n];
  int pivo = A[r];
  int i = 0;
  int j = n - 1;
  
  for (int k = l ; k < r; k ++) {
    if (A [k] <= pivo ) aux [i ++] = A[k ];
    else aux [j - -] = A[ k ];  
  }
  aux [i ] = pivo ;
  i = 0;
  for (int k = l ; k <= r; k ++) A[ k] = aux [i ++];
  return j;
  }
//O(n)
´´´

Pior->  O(n²)
Médio -> O(n logn)

![image](https://user-images.githubusercontent.com/102996679/236327577-f6195b2a-a226-4369-af19-d93aa7e13358.png)
