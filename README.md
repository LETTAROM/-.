# -.
Считать из файла последовательность целых чисел.Вычислить 90 персентиль, медиану, максимальное, ////минимальное и среднее значения.На вход программа получает файл с числами.Каждое число в файле находится ////на новой строке.Вывод в консоль должен быть следующим :

//90 percentile <значение>
//median <значение>
//average <значение>
//max <значение>
//min <значение>


#include <algorithm>
#include <vector>
#include <string>
#include <fstream>
#include <numeric>
#include<iostream>
using namespace std;
int main()
{  
	setlocale(LC_ALL, "rus");
	string path = " ";
	cout<<"Введите путь к файлу, например, S:\\C++\\Pr1\\Pr1\\test.txt"<< endl;
	cin >> path;
	
		ifstream fin;
		fin.open(path);
		vector<double> v ;
			while (!fin.eof())
			{
				string str = " ";
				fin >>  str; 
                int b = atoi(str.c_str());
				getline(fin, str);
				v.push_back(b);
			}
    fin.close();
	int count = 0;
		count = v.size();
	
auto sum= accumulate(v.begin(), v.end(),0);
int average = sum / count;
		  cout << "average "<<"<"<<average<<">" << endl; 
			auto max=max_element(v.begin(), v.end());
			cout << "max  " << "<" << *max << ">" << endl;
			 
			
			auto min = min_element(v.begin(), v.end());
			cout << "min " << "<" << *min << ">" << endl;

			nth_element(v.begin(), v.begin() + v.size() / 2, v.end());
			cout << "median " << "<" << v[v.size() / 2]<< ">" << '\n';
			 
			sort(v.begin(), v.end());


	return 0;
}
