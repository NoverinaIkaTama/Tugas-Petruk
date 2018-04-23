#include <iostream>
#include <cstring>
using namespace std;
int main() {
    
    char Kata1[] = {'t','g','b','w','w','i','n','t','e','r','w','s','e','s','n'};
    char Kata2[] = {'a','a','u','n','t','t','m','m','h','f','o','o','d','n','b'};
    char Kata3[] = {'j','l','w','c','q','l','d','z','m','p','m','v','d','m','r'};
    char Kata4[] = {'a','s','a','g','m','q','u','w','v','v','b','s','o','h','i'};
    char Kata5[] = {'b','w','p','l','o','t','a','n','a','d','t','p','g','n','c'};
    char Kata6[] = {'r','e','w','n','g','o','d','j','c','p','n','a','t','n','k'};
    char Kata7[] = {'e','e','o','t','w','o','s','b','q','h','a','r','r','s','a'};
    char Kata8[] = {'a','z','c','g','e','s','w','e','w','n','a','k','n','p','b'};
    char Kata9[] = {'d','i','n','n','e','r','q','o','d','l','w','d','c','a','r'};
    char Kata10[] = {'o','n','o','p','k','w','m','p','a','r','k','t','z','c','c'};
    char Kata11[] = {'q','b','f','r','o','g','m','a','m','w','p','w','e','e','y'};
    char Kata12[] = {'l','q','z','q','n','n','m','r','z','j','j','s','c','l','g'};
    char Kata13[] = {'m','o','s','g','z','c','z','e','t','d','b','o','o','t','o'};
    char Kata14[] = {'p','d','c','r','z','m','s','n','g','r','d','n','r','p','z'};
    char Kata15[] = {'o','h','n','k','z','w','a','t','e','r','j','g','t','r','a'};
    char *Y[] = { Kata1, Kata2, Kata3, Kata4, Kata5, Kata6, Kata7, Kata8, Kata9, Kata10, Kata11, Kata12, Kata13,Kata14,Kata15};
  	cout <<"====================================~~===================================="<<endl<<endl;
    cout <<"\t\t\t\t Welcome to Game Find Words"<<endl<<endl;
    cout <<"====================================~~===================================="<<endl;
    for(int a = 0; a<15; a++){
        for(int b=0; b<15; b++) 
        cout<<*(*(Y+a)+b)<<" ";
        cout<<endl;
    }
lagi:  
            int juml_kata;
                cout<<endl<<" Berapa kata yang akan anda cari? : ";
                cin>>juml_kata;
            int hasil[juml_kata], hasil_akhir[juml_kata], panjang[juml_kata] ,diagonal;
                char kata[juml_kata][15];

    cin.ignore();
    for(int a=0; a<juml_kata; a++) {
        cout<<a+1<<". ";
        cin.getline(kata[a], 15);
        panjang[a]=strlen(kata[a]);   
    }

    for(int m=0; m<juml_kata; m++) {
        hasil[m]=0;
        int panjang_kata = panjang[m], x=0;
        bool ada[panjang_kata], result;
        
        for(int r = 0 ; r < 15 ; r++){
            for(int a=0; a<=(15-panjang_kata); 
            a++) {
                for(int b=a; b<=a+(panjang_kata-1); 
                b++) {
                    if(*(*(Y+r)+b) == kata[m][x]) ada[x] = 1;
                    else ada[x] = 0;
                    x++;
                }
                for(int k=0; k<panjang_kata; 
                k++) {
                    if(ada[k]==1) {
                        result = 1;
                        hasil[m]+=result;
                    }
                else {
                    result = 0;
                    break;
                    }
                    if(hasil[m]==panjang_kata) { 
                        hasil_akhir[m]=1; 
                        goto next; 
                    }
                }
                hasil[m]=0;
                x=0;
            }
        }

        for(int c = 0 ; c < 15 ; c++){
            for(int a=0; a<=(15-panjang_kata); a++) {
                for(int b=a; b<=a+(panjang_kata-1); b++) {
                    if(*(*(Y+b)+c) == kata[m][x]) ada[x] = 1;
                    else ada[x] = 0;
                    x++;
                }
                for(int k=0; k<panjang_kata; k++) {
                    if(ada[k]==1) {
                        result = 1;
                        hasil[m]+=result;
                    }
                else {
                result = 0;
                    break;
                    }
                    if(hasil[m]==panjang_kata) { 
                        hasil_akhir[m]=1; 
                        goto next; 
                    }
                }
                hasil[m]=0;
                x=0;
            }
        }
        for(int dn = 0 ; dn < 15 ; dn++){
            for(int i=0; i<=(15-panjang_kata); i++) {
            diagonal=-1;
                for(int j=i; j<=i+(panjang_kata-1); j++) {
                    ++diagonal;
                    if(*(*(Y+j)+dn+diagonal) == kata[m][x]) ada[x] = 1;
                    else ada[x] = 0;
                    x++;
                }
                for(int k=0; k<panjang_kata; k++) {
                    if(ada[k]==1) {
                        result = 1;
                        hasil[m]+=result;
                    }
                    else {
                        result = 0;
                        break;
                    }
                    if(hasil[m]==panjang_kata) { 
                        hasil_akhir[m]=1; 
                        goto next; 
                    }
                }
                hasil[m]=0;
                x=0;
            }
        }

        for(int dr = 14 ; dr >= 0 ; dr--){
            for(int i=0; i<=(15-panjang_kata); i++) {
            diagonal=-1;
                for(int j=i; j<=i+(panjang_kata-1); j++) {
                    ++diagonal;
                    if(*(*(Y+j)+dr-diagonal) == kata[m][x]) ada[x] = 1;
                    else ada[x] = 0;
                    x++;
                }
                for(int k=0; k<panjang_kata; k++) {
                    if(ada[k]==1) {
                        result = 1;
                        hasil[m]+=result;
                    }
                else {
                        result = 0;
                        break;
                    }
                if(hasil[m]==panjang_kata) { 
                        hasil_akhir[m]=1; 
                        goto next; 
                    }
                }
                hasil[m]=0;
                x=0;
            }
        }
        next:
        x=0;
    }
cout<<endl<<"Hasil pencarian kata : "<<endl;
    for(int a=0; a<juml_kata; a++) {
        if(hasil_akhir[a]==1)
        {
            cout<<a+1<<". ADA"<<endl;
        }
        else cout<<a+1<<". TIDAK ADA"<<endl;
    }
    char yt;
    cout<<endl;
    cout<<"ingin mencoba lagi?(Y/T) = ";
    cin>>yt;
	cout<<endl;
    if (yt=='y'||yt=='Y'){
    	goto lagi;
	} 
	else (yt=='t'||yt=='T');{
		goto exit;
	}
    
    
    exit:
    	cout<<"Terimakasih";
    return 0;
}

