#include <iostream>
#include <stdio.h>
#include <fstream>
#include <string>
using namespace std;
const int ROWS=15;
const int COLUMNS=15;
const int MAX=5;
int input=0;
string words[MAX];
string kata;

char table[15][15]={{'t','g','b','w','w','i','n','t','e','r','w','s','e','s','n'},
		    {'a','a','u','n','t','t','m','m','h','f','o','o','d','n','b'},
		    {'j','l','w','c','q','l','d','z','m','p','m','v','d','m','r'},
		    {'a','s','a','g','m','q','u','w','v','v','b','s','o','h','i'},
		    {'b','w','p','l','o','t','a','n','a','d','t','p','g','n','c'},
		    {'r','e','w','n','g','o','d','j','c','p','n','a','t','n','k'},
		    {'e','e','o','t','w','o','s','b','q','h','a','r','r','s','a'},
		    {'a','z','c','g','e','s','w','e','w','n','a','k','n','p','b'},
		    {'d','i','n','n','e','r','q','o','d','l','w','d','c','a','r'},
		    {'o','n','o','p','k','w','m','p','a','r','k','t','z','c','c'},
		    {'q','b','f','r','o','g','m','a','m','w','p','w','e','e','y'},
		    {'l','q','z','q','n','n','m','r','z','j','j','s','c','l','g'},
		    {'m','o','s','g','z','c','z','e','t','d','b','o','o','t','o'},
		    {'p','d','c','r','z','m','s','n','g','r','d','n','r','p','z'}};

void initialize(fstream &inputFile){

    for (int i=0; i<ROWS; i++)
    {

        for (int j=0; j<COLUMNS; j++)
            inputFile>>table[i][j];
    }

}

void displayConfig()
{
    for (int i=0; i<ROWS; i++)
    {
        for (int j=0; j < COLUMNS; j++)
        {

            cout << table[i][j];
        }
cout << endl;
    }

} 

int wordcheck(fstream &inputFile){


for(int k=0; k<MAX; k++){
    inputFile>>table[15][15]>>words[k];
    cout<<words[k]<<endl;
}

    }


int checkRow(fstream &inputFile, int i)
{

    string temp = "";
    for(int j=0; j<15 ; j++)
        temp += table[i][j];

    if (temp.find(words[5]) != string::npos){
        return 0;}

        return 1;

}


int checkColumn(fstream &inputFile, int k)

{

    string temp = "";
    for(int t=0; t<15 ; t++)
        temp += table[t][k];


    if (temp.find(words[5]) != string::npos){
    return 0;}

    return 1;
}

int checkRightDiagonal(fstream &inputFile, int i, int j)
{
    string temp = "";

    while (i<15 && j<15)
    {
        temp += table[i][j];
        i++;
        j++;
    }
    if (temp.find(words[5]) != string::npos){
    return 0;}

    return 1;
}

int checkLeftDiagonal(fstream &inputFile, int i , int j)
{
    string temp = "";

    while (i<15 && j>=0)
    {
        temp += table[i][j];
        i++;
        j--;
    }
    if (temp.find(words[5]) != string::npos){
    return 0;
    }
    return 1;
}


int checkConfiguration(fstream &inputFile)
{

    for(int row=0; row<15 ; row++)
    {
        int result = checkRow(inputFile, row);
        if (result != 0)
        {
            return 20;
        }
    }
    for(int column=0; column<15 ; column++)
    {
        int result = checkColumn(inputFile, column);
        if (result != 0)
            return 20;
    }
    for(int row=0; row<15 ; row++)
    {
        for(int column=0; column<15 ; column++)
        {
            int result=checkLeftDiagonal(inputFile, row, column);
            if (result != 0)
                return 20;
        }
    }
    for(int row=0; row<15 ; row++)
    {
        for(int column=0; column<15 ; column++)
        {
            int result=checkRightDiagonal(inputFile, row, column);
            if (result != 0)
                return 20;
        }
    }
}



int main(){
fstream inputFile;
inputFile.open("wordsearch_data.txt");

initialize(inputFile);
displayConfig();

wordcheck(inputFile);

checkConfiguration(inputFile);
}	
