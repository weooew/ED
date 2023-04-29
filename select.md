# Select sort

Trocar v[0] com o menor do v[0],..,v[n-1]

Trocar v[1] com o menor de v[1],..,v[n-1]
...
```cpp
void selectisort(int v[], int ini, int fim){
  for(int i = ini; i < fim; i++){
    int min = i;
    for(int j = i+1; j <= fim; j++){
      if(v[j] < v[min])
        min = j;
      int aux = v[i];
      v[i] = v[min];
      v[min] = aux;
    }
  }
} 
```

