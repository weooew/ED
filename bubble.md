# Bubble-sort
Começa do fim/começo comparando 2 elemento (e trocando se a ordem estiver errada) até que o menor/maior chegue seu lugar devido.
Repita sem mexer nesse lugar...

<img align= "right" width= "300" height= "250" src= "https://user-images.githubusercontent.com/102996679/235320327-115a3075-db8f-42d4-bf68-a19c3f2e4e64.png">

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
```
