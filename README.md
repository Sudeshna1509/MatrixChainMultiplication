# MatrixChainMultiplication
Finding out the minimum # of multiplication in a chain of matrix
#include<iostream>
#include<limits.h>
using namespace std;

int matrixchain(int n,int p[])
{
	int i,j,gap=1,m[50][50],min=INT_MAX,k,x;
	for(i=0;i<n;i++)
	m[i][i]=0;
	i=0;
	j=gap;
	while(gap<n)
	{   
		while(j<n)
		{   k=i;
			while(k<j)
			{
			x=m[i][k]+m[k+1][j]+p[i]*p[k+1]*p[j+1];
			k++;
			if(min>x)
			min=x;
		    }
		    m[i][j]=min;
		    cout<<"m["<<i<<"]["<<j<<"] :"<<m[i][j]<<endl;
		    min=INT_MAX;
         j++;
         i++;
		}
		gap++;
	i=0;
	j=i+gap;	
	}
	return m[0][n-1];
}


int main()
{
	int i,n,j=0,p[50],ret;
	cout<<"Enter the no. of matrices "<<endl;
	cin>>n;
	
	for(i=0;i<n;i++)
	{   
		cout<<"enter the order of "<<i<<"th matrix "<<endl;
		cin>>p[j]>>p[j+1];
		j++;
	}
	
	ret=matrixchain(n,p);
	cout<<"the min no. of multiplication is "<<ret;
}
