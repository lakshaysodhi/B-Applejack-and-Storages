# B-Applejack-and-Storages
#include <bits/stdc++.h>
using namespace std;


int main(){

    int n;
    unordered_map<int,int> umap;
    cin>>n;
    vector<int> planklength(n);
    int four=0,two=0;//we need 4 same for the square and rest we need 2 of 2 same or they all could be same but after removing those four
    for(int i=0;i<n;i++){

        cin>>planklength[i];
        if(umap.count(planklength[i])==0){
            umap[planklength[i]]=1;
        }else{
            umap[planklength[i]]++;
        }

    }
    for(auto i=umap.begin();i!=umap.end();i++){
       two+=(i->second)/2;
       four+=(i->second)/4;
    }
    int numofevents;
    cin>>numofevents;
    vector<int> events(numofevents);
    vector<char> sign(numofevents);
    for(int i=0;i<numofevents;i++){
        cin>>sign[i]>>events[i];
    }
    for(int i=0;i<numofevents;i++){
        if(sign[i]=='+') {

                if(umap.count(events[i])==0){
                    umap[events[i]]=1;
                }else{
                    two-=umap[events[i]]/2;
                    four-=umap[events[i]]/4;
                    umap[events[i]]++;
                    two+=umap[events[i]]/2;
                    four+=umap[events[i]]/4;

                }
        }
        else {
                two-=umap[events[i]]/2;
                four-=umap[events[i]]/4;
                umap[events[i]]--;
                two+=umap[events[i]]/2;
                four+=umap[events[i]]/4;
        }
    if(four>0 && (two-2)>1){
        cout<<"YES"<<endl;
    }else cout<<"NO"<<endl;

    }
}
