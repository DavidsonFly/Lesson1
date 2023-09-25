// Task 1.cpp : Этот файл содержит функцию "main". Здесь начинается и заканчивается выполнение программы.
//

#include <iostream>
#include <fstream>
#include <vector>

int main()
{
	// Открываю тестовый файл.
	std::ifstream in ("in.txt");

	//Проверяю файл на открытие.
	if (in.is_open())
	{
		std::cout << "File is open" << std::endl;
	}
	else
	{
		std::cout << "File not open" << std::endl;
	}
	
	//Объявление переменных для записи в них размера массивов из файла.
	int size1;
	int size2;
	in >> size1; // Запись первого массива в переменную.
	std::vector <int> arr1(size1); //Инициализация массива 1.

	// Запись в первый массив.
	for (int i = 0; i < size1; i++)
	{
		in >> arr1[i];
	}
	
	 //Запись во второй массив.
	in >> size2;
	std::vector <int> arr2(size2);
	for (int i = 0; i < size2; i++)
	{
		in >> arr2[i];
	}
	in.close(); //Закрываю файл.

	//Сдвиг элементов второго массива.
	int lastElement = arr2[size2 - 1];
	for (int i = size2 - 1; i >= 1; i--)

	{
		arr2[i] = arr2[i-1];
	}
	arr2[0] = lastElement;

	std::cout << size2 << std::endl;
	for (int i = 0; i < size2; i++)
	{
		std::cout << arr2[i] << " ";
	}
	std::cout << std::endl;
	
	//Сдвиг элементов первого массива.
	
	std::cout << size1 << std::endl;


	int firstElement = arr1[0];
	for (int i = 0; i < size1 - 1; i++)
	{
		arr1[i] = arr1[i + 1];
	}
	arr1[size1 - 1] = firstElement;

	for (int i = 0; i < size1; i++)
	{
		std::cout << arr1[i] << " ";
		if (i!= size1 - 1)
		{
			std::cout << " ";
		}
	}
	std::cout << std::endl;

	//Запись массивов в выходной файл.

	std::ofstream out("out.txt");
	if (out.is_open())
	{
		std::cout << "Out file is opened" << std::endl;
	}
	else
	{
		std::cout << "Do not opened" << std::endl;
	}

	//Запись второго массива.
	 size2 = arr2.size();
	out << size2 << std::endl;
	for (int i = 0; i < size2; i++)
	{
		out << arr2[i] << " ";
	}
	out << std::endl;

	//Запись первого массива.
	 size1 = arr1.size();
	out << size1 << std::endl;
	for (int i = 0; i < size1; i++)
	{
		out << arr1[i] << " ";
	}
	out << std::endl;
	out.close();

	return 0;
}