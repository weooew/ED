# Árvores Binárias

Definição recursiva conjunto finito de elementos(nós), vazio ou um nó raiz com 2 subárvores binárias
Nós folhas: últimos da árvore
Nós internos:
(filho, pai, neto, avô, irmão, tio, ancestrais, descendentes..)

Profundidade: de um nó A, N° de nós no caminho de A até a raiz (contando com si mesmo)
Altura: N° de nós no maior caminho de A até uma folha descendente (contando com si mesmo)
Nível: 1,2,3,4...
OBS: ordem dos filhos é relevante!

Arvore binária completa: se A e um nó tal que alguma sub ́arvore de A é vazia, ent ̃ao v se localiza ou no pen ́ultimo
ou no  ́ultimo n ́ıvel da  ́arvore.
Árvore binária cheia: todos os seus nós internos têm dois filhos e todas as folhas estão no último nível da árvore.


Relação entre altura e nós:
Se altura h: no mínimo h nós, no máximo 2^h-1 nós
Se tem n >= 1 nós então:
  altuna no mínimo(log2(n+1)), no máximo(n)

IMPLEMENTAÇÃO
cada nó terá: valor, pont p/ filho esq e pont p/ filho dir

head: pont para nó raiz
//pode ter pont para pai (raiz apont para null)

´´´

´´´
´´´

´´´

PERCURSOS EM ÁRVORES BINÁRIAS
Comum percorrer uma árvore em uma das seguintes ordens: 
  pré-ordem: trata raiz, percorre r->left, percorre r->right (1° raiz, depois subárvore esq, depois subárvore dir)
  ordem simétrica: percorre r->left, trata raiz, percorre r->right (primeiro visita a subárvore esquerda; depois visita a raiz; e por última visita a subárvore direita)
  pós-ordem: percorre r->left, percorre r->right, trata raiz (1° subárvore esq, depois a subárvore direita, por último visita a raiz)

pré-ordem: 2,5,3,8,4,7,1,9,6 (RA, L, R)
pós-ordem: 3,4,8,5,9,1,6,7,2 (L, R, RA)
simétrica: 3,5,4,8,2,1,9,7,6 (L, RA, R)

       _2_
  _5_      _7_
3     _8  1_   6
     4      9
PERCURSO EM LARGURA
Visita nós por níveis, da esquerda para a direita


´´´
#include <iostream>
#include <string>
#include <vector>
#include "binarytree.h"
using namespace std;

template<typename T>
void bt_pre_ordem(BinaryTree<T>& bt){
    Node<T>* root = bt.getRoot();
    if(root != nullptr){
        vector<Node<T>*> vec;
        vec.push_back(root);
        
        while(vec.empty() != 1){
            Node<T>* p = vec.back();
            vec.pop_back();
            cout << p->getValue() << " ";
            
            if(p->getRight() != nullptr) vec.push_back(p->getRight());
            if(p->getLeft() != nullptr) vec.push_back(p->getLeft());
        }   
    }
}

template<typename T>
void bt_pos_ordem(BinaryTree<T>& bt) {
    Node<T>* root = bt.getRoot();
    if(root != nullptr){
        vector<Node<T>*> vec;
        Node<T>* p = root;
        Node<T>* p2 = nullptr;
        
        while(p != nullptr || vec.empty() != 1){
            if(p != nullptr){
                vec.push_back(p);
                p = p->getLeft();
            } 
            else{
                Node<T>* temp = vec.back()->getRight();
                if(temp == nullptr || temp == p2){
                    p = vec.back();
                    vec.pop_back();
                    cout << p->getValue() << " ";
                    p2 = p;
                    p = nullptr;
                }
                else {
                    p = temp;
                }
            }
        }
    }
}

template<typename T>
void bt_ordem_simetrica(BinaryTree<T>& bt) {
    Node<T>* root = bt.getRoot();
    if(root != nullptr){
        vector<Node<T>*> vec;
        Node<T>* p = root;
        
        while(p != nullptr || vec.empty() != 1){
            if(p != nullptr){
                vec.push_back(p);
                p = p->getLeft();
            } 
            else{
                p = vec.back();
                vec.pop_back();
                cout << p->getValue() << " ";
                p = p->getRight();
            }
        }
    }
}

template<typename T>
void bt_percurso_largura(BinaryTree<T>& bt) {
    Node<T>* root = bt.getRoot();
    if(root != nullptr){
        vector<Node<T>*> vec;
        vec.push_back(root);
        
        while(vec.empty() != 1){
            Node<T>* p = vec.front();
            vec.erase(vec.begin());
            cout << p->getValue() << " ";
            if (p->getLeft() != nullptr) vec.push_back(p->getLeft());
            if (p->getRight() != nullptr) vec.push_back(p->getRight());
        }
    }
}


template<typename T>
void execute_all(BinaryTree<T>& bt){
    bt_pre_ordem(bt);
    cout << "\n";
    bt_pos_ordem(bt);
    cout << "\n";
    bt_ordem_simetrica(bt);
    cout << "\n";
    bt_percurso_largura(bt);
}

int main(){
    Node<int>* no9 = new Node<int>(9, nullptr, nullptr);
    Node<int>* no1 = new Node<int>(1, nullptr, no9);
    Node<int>* no6 = new Node<int>(6, nullptr, nullptr);
    Node<int>* no7 = new Node<int>(7, no1, no6);
    
    Node<int>* no4 = new Node<int>(4, nullptr, nullptr);
    Node<int>* no8 = new Node<int>(8, no4, nullptr);
    Node<int>* no3 = new Node<int>(3, nullptr, nullptr);
    Node<int>* no5 = new Node<int>(5, no3, no8);
    
    Node<int>* no2 = new Node<int>(2, no5, no7);
    
    BinaryTree<int> bt;
    bt.setRoot(no2);
    execute_all(bt);
}
´´´










