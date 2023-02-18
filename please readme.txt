#include <iostream>
#include <string>
using namespace std;
int main()
{
 int num ;
 float amount ;
 cout<<"enter num 1 for BTC"<<endl;
  cout<<"enter num 2 for ETH"<<endl;
   cout<<"enter num 3 for USDT"<<endl;
cout<<"enter currancy number : ";
cin>> num;
switch (num)
{
	case 1: 
	cout<<"***************BTC***************"<<endl;
	cout<<"ENTER AMOUNT : ";
	cin>>amount;
	cout<<"the amount is "<<amount *24.637<<endl;break;
	case 2:
		cout<<"***************USDT***************"<<endl;
	cout<<"ENTER AMOUNT : ";
	cin>>amount;
	cout<<"the amount is "<<amount *1.69<<endl;break;
	case 3:
		cout<<"***************ETH***************"<<endl;
	cout<<"ENTER AMOUNT : ";
	cin>>amount;
	cout<<"the amount is "<<amount*	1.0002<<endl;break;
	default :
		cout<<"ERROR";
}


system("pause");
return 0;






}
