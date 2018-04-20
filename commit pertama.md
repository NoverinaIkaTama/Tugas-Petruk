# Tugas-Petruk

#include <iostream>
using namespace std;
int main() {
  int puzzle[10][10] ={{'A','F','T','Y','S','A','R','A','T','E'},
						 {'N','U','I','N','P','U','T','R','E','G'},
						 {'E','N','K','Z','R','T','I','R','M','U'},
						 {'S','C','W','A','I','E','S','A','P','P'},
						 {'I','T','B','I','N','A','R','Y','L','O'},
						 {'A','I','N','T','E','G','E','R','A','I'},
						 {'V','O','I','D','C','F','W','X','T','N'},
						 {'B','N','K','L','S','Q','T','Z','E','T'},
						 {'I','C','O','D','I','N','G','W','S','E'},
						 {'W','E','S','T','R','I','N','G','J','O'}};
						 
					int i,j;
					string tmp;
					for(i=0;i<10;i++){
						tmp.clear();
						for(j=0;j<10;j++){
							tmp+=puzzle[i][j];
						}
						cout<<tmp<<endl;
  
return 0;
}
