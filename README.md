#sqrt
#快速排序
#include <iostream>
#include<stdio.h>
#include<stdlib.h>
#include<string.h>
#include<vector>
#include<cmath>
#include<iomanip>
#include<algorithm>
#include<functional>
#include<sstream>
#include<map>
using namespace std;

int sqrt(int a[],int first,int last){
	if(first>=last){
		return 0;
	}
	int low=first;
	int top=last;//记录起始和终止位置 
	int p=a[first];
	while(first<last){
		while(first<last&&a[last]>=p){
			--last;
		}
		a[first]=a[last];//用后面那个小的覆盖前面的first 
		while(first<last&&a[first]<=p){
			++first;
		}
		a[last]=a[first];//用前面的大的覆盖后面的（上面算出来的）小的位置 
	}
	a[first]=p;//这时first上的值还是大的那个（上面最后一步覆盖的），用p代替即可 
	sqrt(a,low,first-1);
	sqrt(a,first+1,top); 

	
}

int main() {
	int n;
	cin>>n;
	int a[n];
	for(int i=0;i<n;i++){
		cin>>a[i];
	}
	sqrt(a,0,n-1);
	for(int i=0;i<n;i++){
		cout<<a[i]<<" ";
	}
	
	
	return 0;
}
