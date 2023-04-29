# Bubble-sort
Começa do fim comparando 2 elemento (e trocando se a ordem estiver errada) até que o menor chegue no 1 lugar.
Repita sem mexer no 1 lugar...

|_5_|_2_|_3_|_1_|
|_5_|_2_|_1_|_3_|
|_5_|_1_|_2_|_3_|
|_1_|_5_|_2_|_3_|

|_1_|_5_|_2_|_3_|
|_1_|_2_|_5_|_3_|

|_1_|_2_|_3_|_5_|


```cpp
#include <iostream>
using namespace std;

void bubblesort(int v[], int ini, int fim){
  int z;
    for(int x = ini; x < fim; x++){
        z = fim -1;
        for(int y = fim; y > x; y--){
            if(v[y] < v[z]){
                int a = v[z];
                v[z] = v[y];
                v[y] = a;
            }
            z--;
        }
    }
}

int main(){
    int n;
    scanf("%d", &n);
    int vetor[n];
    for(int i = 0; i < n; i++){
        scanf("%d", &vetor[i]);
    }
    bubblesort(vetor, 0, n-1);
    
    for(int i = 0; i < n; i++) printf("%d ", vetor[i]);

    return 0;
}
```
Se não ocorreu nenhuma troca podemos parar o algoritmo
```cpp
void bubblesort_v2(int v[], int ini, int fim){
  bool trocou = false;
  int z;
    for(int x = ini; x < fim; x++){
        z = fim -1;
        for(int y = fim; y > x; y--){
            if(v[y] < v[z]){
                int a = v[z];
                v[z] = v[y];
                v[y] = a;
                trocou = true;
            }
            z--;
        }
    }
}




