# Kelompok-Expresi-Matematika

//Nomor 1 Parsing String Infix
//Fitriah Hardianti (2057051001)

#include <iostream>
#include <vector>
#include <cstring>
using namespace std;

void Separate (string masuk){
    vector<char> sprtd;
    string d;

    char isNumber[] = "0123456789";
    char isSymbol[] = "+-/%*";
    char isSpacing[] = "()";
    char character[1];
    
    for(auto charMasuk : masuk){
        character[0] = charMasuk;

        if(strspn(character, isSymbol) || strspn(character, isNumber) || strspn(character, isSpacing)){
            sprtd.push_back(charMasuk);
        }
    }
    
    int len = sprtd.size();
    for (int n = 0; n != len; n++){    
        character[0] = sprtd[n];

        if((strspn(character, isSymbol) || sprtd[n] == ')') && sprtd[n] != '(' && n > 0){
            d += " ";
        }
        
        if(strspn(character, isNumber)){
            d += sprtd[n];
        }else{
            d += sprtd[n];
            if(n > 0){
                character[0] = sprtd[n - 1];

                if(sprtd[n] != '(' && strspn(character, isSymbol)){
                    d += "1 * ";
                }else if(sprtd[n] != ')'){
                    character[0] = sprtd[n + 1];

                    if(!strspn(character, isSymbol)){
                        d += " ";
                    }
                }
            }else if(sprtd[n + 1] == '('){
                d += "1 * ";                
            }
        }
    }

    cout << d << endl;
}

int main(){
    string masuk;

    getline(cin, masuk);
 
    
    Separate(masuk);
}
  
  
