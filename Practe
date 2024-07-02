#include <iostream>
#include <fstream>
#include <string>
#include <windows.h>
#include <cstdio>
#include <conio.h>
#include <time.h>
#include <stdio.h>
#pragma warning(disable:4996)
using namespace std;
int Stop = 3;
char GlavWAY[100] = "D:\\Praktika";
char WAY[100];
wchar_t LWAY[100];
string Rule, Use, buff, save, last;
int T = 0, ATO = 0;
void Clear(int G)
{
	int i = 0;
	if (G == 0)
	{
		FillMemory(WAY, 100, 0);
	}
	else if (G == 1)
	{
		FillMemory(LWAY, 100, 0);
	}
}
string Trans(string way, int R)
{
	if (R == 0)
	{
		way = way + "\\*";
		int i = 0;
		Clear(1);
		while (i != way.length())
		{
			LWAY[i] = way[i];
			i++;
		}
	}
	else if (R == 1)
	{
		int i = 0;
			Clear(0);
		while (i != way.length())
		{
			WAY[i] = way[i];
			i++;
		}
	}
	else if (R == 3)
	{
		int i = 0;
		while (i != 100)
		{
			WAY[i] = LWAY[i];
			i++;
		}
		way = WAY;
	}
	else if (R == 2)
	{
		int i = 0;
		Clear(1);
		last = last + "\\*";
		while (i != last.length())
		{
			LWAY[i] = last[i];
			i++;
		}
	}
	return way;
}
void List(string way)
{
	Trans(way, 0);
	WIN32_FIND_DATAW wfd;
	HANDLE const hFind = FindFirstFileW(LWAY, &wfd);
	setlocale(LC_ALL, "");
	int i = 0;
	if (INVALID_HANDLE_VALUE != hFind)
	{
		do
		{
			if (i >= 2)
				std::wcout << &wfd.cFileName[0] << std::endl;
			i++;
		} while (NULL != FindNextFileW(hFind, &wfd));
		FindClose(hFind);
	}
}
void Travel(string way, int R)
{
	if (R == 0)
	{
		if (T == 0)
		{
			buff = GlavWAY;
			way = buff + "\\" + way;
			Trans(way, 0);
			WIN32_FIND_DATAW wfd;
			HANDLE const hFind = FindFirstFileW(LWAY, &wfd);
			if (INVALID_HANDLE_VALUE != hFind)
			{
				List(way);
				T++;
			}
			else
			{
				cout << "Папка не существует" << endl;
				cout << "Путь: " << way << endl;
				List(way);
			}
		}
		else
		{
			buff = Trans(buff, 3);
			buff.erase(buff.rfind("\\"));
			way = buff + "\\" + way;
			Trans(way, 0);
			WIN32_FIND_DATAW wfd;
			HANDLE const hFind = FindFirstFileW(LWAY, &wfd);
			if (INVALID_HANDLE_VALUE != hFind)
			{
				List(way);
				T++;
			}
			else
			{
				cout << "Папка не существует." << endl;
				way.erase(way.rfind("\\"));
				List(way);
			}
		}
	}
	else if (R == 1)
	{
		way.erase(way.rfind("\\"));
		way.erase(way.rfind("\\"));
			List(way);
		T--;
	}
}
int Prov(string way, int R)
{
	if (R == 0)
	{
		if (way == "D:\\учеба\\Универ\\Практика 3 курс\\Программа\\Data.txt")
		{
			cout << "Файл недоступен для данной команды." << endl;
			return 1;
		}
		else if (way == "D:\\учеба\\Универ\\Практика 3 курс\\Программа\\Journal.txt")
		{
			cout << "Файл недоступен для данной команды." << endl;
			return 1;
		}
		string line;
		ifstream myfile(way);
		if (myfile.is_open())
		{
			myfile.close();
			return 0;
		}
		else cout << "Файл с данным названием не найден." << endl;
		return 1;
	}
	else if (R == 1)
	{
		if (way == "D:\\учеба\\Универ\\Практика 3 курс\\Программа\\Data.txt")
		{
			cout << "Файл недоступен к редактированию." << endl;
			return 1;
		}
		else if (way == "D:\\учеба\\Универ\\Практика 3 курс\\Программа\\Journal.txt")
		{
			cout << "Файл недоступен к редактированию." << endl;
			return 1;
		}
		string line;
		ifstream myfile(way);
		if (myfile.is_open())
		{
			myfile.close();
				return 0;
		}
		else cout << "Файл с данным названием не найден." << endl;
		return 1;
	}
	else if (R == 2)
	{
		if (way == "D:\\учеба\\Универ\\Практика 3 курс\\Программа\\Data.txt")
		{
			cout << "Файл не может быть создан." << endl;
			return 1;
		}
		else if (way == "D:\\учеба\\Универ\\Практика 3 курс\\Программа\\Journal.txt")
		{
			cout << "Файл не может быть создан." << endl;
			return 1;
		}
		string line;
		ifstream myfile(way);
		if (myfile.is_open())
		{
			while (true)
			{
				cout << "Файл будет перезаписан. Продолжить? (y / n)" << endl;
					cin >> line;
				if (line == "y")
				{
					myfile.close();
					return 0;
				}
				else if (line == "n")
				{
					myfile.close();
					return 1;
				}
				else
				{
					cout << "Неверный ввод команды." << endl;
				}
			}
		}
		else return 0;
	}
}
void Journal(string text, int J)
{
	time_t td;
		td = time(NULL);
	string t = ctime(&td);
	if (J == 0)
	{
		if (ATO == 0)
		{
			ofstream myfile("D:\\учеба\\Универ\\Практика 3 курс\\Программа\\Journal.txt", ios_base::app);
			text = "Попытка входа пользователя " + text + " " + t;
			myfile << text;
			myfile.close();
			ATO++;
		}
		else if (ATO == 4)
		{
			ofstream myfile("D:\\учеба\\Универ\\Практика 3 курс\\Программа\\Journal.txt", ios_base::app);
			text = "Попытка входа пользователя " + text + "успешна. " + t;
				myfile << text;
			myfile.close();
		}
	}
	else if (J == 1)
	{
		ofstream myfile("D:\\учеба\\Универ\\Практика 3 курс\\Программа\\Journal.txt", ios_base::app);
		text = "Сессия пользователя " + text + " завершена " + t;
		myfile << text;
		myfile.close();
	}
	else if (J == -1)
	{
		ofstream myfile("D:\\учеба\\Универ\\Практика 3 курс\\Программа\\Journal.txt",
			ios_base::app);
		text = "Попытка входа пользователя неосуществлена " + t;
		myfile << text;
		myfile.close();
	}
	else if (J == 2)
	{
		ofstream myfile("D:\\учеба\\Универ\\Практика 3 курс\\Программа\\Journal.txt", ios_base::app);
		save = text;
		text.erase(text.find("*"));
		if (save.erase(0, save.rfind("*") + 1) == "A")
		{
			text = "Права пользователя " + text + " были изменены с прав пользователя на права администратора. " + t;
		}
		else
		{
			text = "Права пользователя " + text + " были изменены с прав администратора на права пользователя. " + t;
		}
		myfile << text;
		myfile.close();
	}
	else if (J == 3)
	{
		ofstream myfile("D:\\учеба\\Универ\\Практика 3 курс\\Программа\\Journal.txt", ios_base::app);
		text = "Содержимое файла " + text + " было просмотрено пользователем " + Use + " " + t;
			myfile << text;
		myfile.close();
	}
	else if (J == 4)
	{
		ofstream myfile("D:\\учеба\\Универ\\Практика 3 курс\\Программа\\Journal.txt", ios_base::app);
		text = "Содержимое файла " + text + " было редактировано пользователем " + Use + " " + t;
			myfile << text;
		myfile.close();
	}
	else if (J == 5)
	{
		ofstream myfile("D:\\учеба\\Универ\\Практика 3 курс\\Программа\\Journal.txt", ios_base::app);
		text = "Файл " + save + " было удален пользователем " + Use + " из папки " + last.erase(last.rfind("\\")) + " " + t;
		myfile << text;
		myfile.close();
	}
	else if (J == 6)
	{
		ofstream myfile("D:\\учеба\\Универ\\Практика 3 курс\\Программа\\Journal.txt", ios_base::app);
		text = "Пустой файл " + save + " было создан пользователем " + Use + " в папке " + last.erase(last.rfind("\\")) + " " + t;
		myfile << text;
		myfile.close();
	}
	else if (J == 7)
	{
		ofstream myfile("D:\\учеба\\Универ\\Практика 3 курс\\Программа\\Journal.txt", ios_base::app);
		text = "Файл " + save + " было создан пользователем " + Use + " в папке " + last.erase(last.rfind("\\")) + " " + t;
		myfile << text;
		myfile.close();
	}
}
int Remove(string way, int R)
{
	if (R == 1)
	{
		Trans(last, 1);
		remove(WAY);
		return 0;
	}
	else if (R == 2)
	{
		save = way;
		last = Trans(way, 3);
		last = last.erase(last.rfind("*")) + way;
		if (Prov(last, 0) == 0)
		{
			Trans(last, 1);
			remove(WAY);
			Journal(way, 5);
			return 0;
		}
	}
}
int read(string way)
{
	if (way == "Data.txt")
	{
		cout << "Файл недоступен к просмотру." << endl;
	}
	else if (way == "Journal.txt" && Rule == "A")
	{
		string line;
		line = Trans(way, 3);
		way = line.erase(line.rfind("*")) + way;
		ifstream myfile(way);
		if (myfile.is_open())
		{
			while (getline(myfile, line))
			{
				cout << line << '\n';
			} myfile.close();
			Journal(way, 3);
		}
		else cout << "Файл с данным названием не найден.";
	}
	else if (way == "Journal.txt" && Rule == "U")
	{
		cout << "Файл недоступен к просмотру." << endl;
	}
	else
	{
		string line;
		line = Trans(way, 3);
		way = line.erase(line.rfind("*")) + way;
		ifstream myfile(way);
		if (myfile.is_open())
		{
			while (getline(myfile, line))
			{
				cout << line << '\n';
			} myfile.close();
			Journal(way, 3);
		}
		else cout << "Файл с данным названием не найден.";
	}
	return 0;
}
int write(string way)
{
	string line;
	line = Trans(way, 3);
	way = line.erase(line.rfind("*")) + way;
	if (Prov(way, 1) == 0)
	{
		while (true)
		{
			cout << "Перезаписать файл(r); дополнить файл(i); выйти из режима редактирования(e)." << endl;
				char i;
			cin >> i;
			if (i == 'r')
			{
				ofstream myfile(way);
				string text;
				cout << "Введите содержимое файла." << endl;
				cin >> text;
				myfile << text;
				myfile.close();
				Journal(way, 4);
				break;
			}
			else if (i == 'i')
			{
				ofstream myfile(way, ios_base::app);
				string text;
				cout << "Введите содержимое файла." << endl;
					cin >> text;
				text = " " + text;
				myfile << text;
				myfile.close();
				Journal(way, 4);
				break;
			}
			else if (i == 'e')
				break;
			else
				cout << "Неверный ввод команды." << endl;
		}
		return 0;
	}
	else return 1;
}
int creat(string way, int R)
{
	if (R == 0)
	{
		save = way;
		last = Trans(way, 3);
		last = last.erase(last.rfind("*")) + way;
		if (Prov(last, 2) == 1)
		{
			return 1;
		}
		ofstream myfile(last);
		string text = "";
		myfile << text;
		myfile.close();
		Journal(way, 6);
		return 0;
	}
	else if (R == 1)
	{
		save = way;
		last = Trans(way, 3);
		last = last.erase(last.rfind("*")) + way;
		if (Prov(last, 2) == 1)
		{
			return 1;
		}
		ofstream myfile(last);
		string text;
		cout << "Введите содержимое файла." << endl;
		cin >> text;
		myfile << text;
		myfile.close();
		Journal(way, 7);
		return 0;
	}
}
int Data()
{
	string log, pas;
	string line;
	ifstream myfile("D:\\учеба\\Универ\\Практика 3 курс\\Программа\\Data.txt");
	if (myfile.is_open())
	{
		myfile.close();
	}
	else
	{
		return 3;
	}
	int i = 0;
	int Suc = 1;
	while (i != 4)
	{
		cout << "Введите логин." << endl;
		cin >> log;
		cout << "Введите пароль." << endl;
		cin >> pas;
		ifstream myfile("D:\\учеба\\Универ\\Практика 3 курс\\Программа\\Data.txt");
		myfile.is_open();
		while (getline(myfile, line))
		{
			string Erase = line;
			line.erase(line.find("*"));
			if (log == line)
			{
				save = log;
				Journal(save, 0);
				line = Erase;
				line.erase(0, line.find("*") + 1);
				Erase = line;
				line.erase(line.find("*"));
				if (pas == line)
				{
					Rule = Erase.erase(0, Erase.find("*") +1);
					Suc = 0;
					Use = log;
					break;
				}
			}
			// Проверка статуса блокировки
			string blockStatus = line.substr(line.rfind("*") + 1);
			if (blockStatus == "1") {
				cout << "Пользователь заблокирован." << endl;
				return 2; // Новый код возврата для заблокированного пользователя
			}
		}
		myfile.close();
		i++;
		if (Suc == 0)
		{
			Journal(save, 0);
			break;
		}
		else if (i != 3)
			cout << "Неверный логин и/или пароль. У вас осталось" << 3 - i << " попыток." << endl;
			if (i == 3)
			{
				Journal(save, -1);
				return 1;
			}
	}
	return 0;
}
void ListUse(string Way, int R)
{
	if (R == 0)
	{
		ifstream myfile("D:\\учеба\\Универ\\Практика 3 курс\\Программа\\Data.txt");
		myfile.is_open();
		string Say;
		while (getline(myfile, Say))
		{
			Way = Say;
			if (Say.erase(0, Say.rfind("*") + 1) == "A")
			{
				cout << "Пользователь " <<
					Way.erase(Way.find("*")) << " имеет права администратора" << endl;
			}
			else if (Say.erase(0, Say.rfind("*") + 1) == "U")
			{
				cout << "Пользователь " <<
					Way.erase(Way.find("*")) << " имеет права пользователя" << endl;
			}
			else
			{
				cout << "Ошибка чтения прав пользователя " <<
					Way.erase(Way.find("*")) << ". Возможна внешняя модификация данных." << endl;
			}
		}
		myfile.close();
	}
	else if (R == 1)
	{
		ifstream myfile("D:\\учеба\\Универ\\Практика 3 курс\\Программа\\Data.txt");
		myfile.is_open();
		string Say, Pr;
		int S = 0, i = 0, k;
		while (getline(myfile, Say))
		{
			save = Say;
			if (Way == Say.erase(Say.find("*")))
			{
				Say = save;
				Pr = Say.erase(0, Say.rfind("*") + 1);
				save.erase(save.rfind("*"));
				i++;
				k = S;
				break;
			}
			S++;
		}
		if (i == 0)
		{
			cout << "Пользователь " << Way << " не найден." <<
				endl;
			myfile.close();
		}
		else
		{
			string* Slot = new string[S + 1];
			i = 0;
			myfile.seekg(0);
			while (getline(myfile, Say))
			{
				if (k == i)
				{
					Say = Say.erase(Say.rfind("*"));
					if (Pr == "U")
						Say = Say + "*A";
					else
						Say = Say + "*U";
				}
				Slot[i] = Say;
				i++;
			}
			myfile.close();
			ofstream myfile;
			myfile.open("D:\\учеба\\Универ\\Практика 3 курс\\Программа\\Data.txt");
			i = 0;
			while (i != S + 1)
			{
				myfile << Slot[i] << "\n";
				i++;
				myfile.seekp(0, ios::end);
			}
			Journal(Slot[k], 2);
			myfile.close();
				delete[] Slot;
		}
	}
}
void blockUser(string username, bool block) {
	ifstream inFile("Data.txt");
	ofstream outFile("Data_temp.txt");

	string line;
	while (getline(inFile, line)) {
		size_t pos = line.find("*");
		string currentUser = line.substr(0, pos);

		if (currentUser == username) {
			// Изменяем статус блокировки
			size_t lastPos = line.rfind("*");
			line = line.substr(0, lastPos + 1) + (block ? "1" : "0");
		}

		outFile << line << endl;
	}

	inFile.close();
	outFile.close();

	remove("Data.txt");
	rename("Data_temp.txt", "Data.txt");

	cout << (block ? "Пользователь заблокирован" : "Пользователь разблокирован") << endl;
}
int main()
{
	string Way;
	setlocale(LC_ALL, "Russian");
	int Succesful = Data();
	if (Succesful == 1)
	{
		cout << "Попытки аутентификации исчерпаны.";
		system("pause");
		return 1;
	}
	else if (Succesful == 3)
	{
		cout << "Данные утрачены. Аутентификация невозможна." << endl;
		system("pause");
		return 3;
	}
	buff = GlavWAY;
	List(buff);
	string Answer;
	if (Rule == "A")
	{
		while (true)
		{
			cout << "Выберете доступное действие." << endl;
			cout << "1. Работа с файлами." << endl << "2. Переход в папку." << endl << "3. Измение полномочий пользователей." << endl << "4. Заблокировать/разблокировать пользователя." << endl << "5. Завершение работы." << endl;
				cin >> Answer;
			if (Answer == "1")
			{
				while (true)
				{
					cout << "Выберете доступное действие." << endl;
					cout << "1. Создание файла." << endl << "2. Редактирование файла." << endl << "3. Просмотр содержимого файла." << endl << "4. Удаление файла." << endl << "5. Завершение работы с файлами." << endl;
						cin >> Way;
					if (Way == "1")
					{
						cout << "Введите название файла для создания." << endl;
							cin >> Way;
							while (true)
							{
								cout << "Создать пустым?(y/n)" << endl;
								cin >> Answer;
								if (Answer == "y")
								{
									if (creat(Way, 0) == 0)
									{
										cout << "Файл был успешно создан." << endl;
											break;
									}
									else break;
								}
								else if (Answer == "n")
								{
									if (creat(Way, 1) == 0)
									{
										cout << "Файл был успешно создан." << endl;
											break;
									}
								}
								else
									cout << "Неверный ввод команды." << endl;
							}
					}
					else if (Way == "2")
					{
						cout << "Введите название файла (с расширением) для редактирования." << endl;
							cin >> Way;
						write(Way);
					}
					else if (Way == "3")
					{
						cout << "Введите название файла (с расширением) для просмотра." << endl;
							cin >> Way;
						read(Way);
					}
					else if (Way == "4")
					{
						cout << "Введите название файла (с расширением) для удаления." << endl;
							cin >> Way;
						Remove(Way, 2);
					}
					else if (Way == "5")
					{
						if (Way == "exit")
							cout << "Выход в меню." << endl;
						break;
					}
					else
						cout << "Неверный ввод команды. (Введите цифры из предоставленных.)" << endl;
				}
			}
			else if (Answer == "2")
			{
				if (T == 0)
				{
					cout << "Введите название папки для перехода." << endl;
						cin >> Way;
					Travel(Way, 0);
				}
				else
				{
					cout << "Вернуться в каталог выше?(y/n)" << endl;
					cin >> Way;
					if (Way == "y")
					{
						Way = Trans(Way, 3);
						Travel(Way, 1);
					}
					else if (Way == "n")
					{
						cout << "Введите название папки для перехода." << endl;
							cin >> Way;
						Travel(Way, 0);
					}
					else
					{
						cout << "Неверный ввод команды." << endl;
					}
				}
			}
			else if (Answer == "3")
			{
				ListUse(Way, 0);
				cout << "Введите логин пользователя для изменения прав. Или выйти из режима редактирования прав(exit) ? " << endl;
				cin >> Way;
				if (Way == "exit")
					cout << "Выход в меню." << endl;
				else
					ListUse(Way, 1);
			}
			else if (Answer == "4") 
			{
				cout << "Введите команду (block/unblock username):" << endl;
				string command, username;
				cin >> command >> username;

				if (command == "block") {
					blockUser(username, true);
				}
				else if (command == "unblock") {
					blockUser(username, false);
				}
			}
			else if (Answer == "5")
			{
				cout << "Завершение работы." << endl;
				Journal(Use, 1);
				system("pause");
				return 0;
			}
		
			else
				cout << "Неверный ввод команды. (Введите цифры из предоставленных)" << endl;
		}
	}
	else if (Rule == "U")
	{
		while (true)
		{
			cout << "Выберете доступное действие." << endl;
			cout << "1. Работа с файлами." << endl << "2. Переход в папку." << endl << "3. Завершение работы." << endl;
				cin >> Answer;
			if (Answer == "1")
			{
				while (true)
				{
					cout << "Выберете доступное действие." << endl;
					cout << "1. Создание файла." << endl << "2. Редактирование файла." << endl << "3. Просмотр содержимого файла." << endl << "4. Удаление файла." << endl << "5. Завершениеработы с файлами." << endl;
						cin >> Way;
					if (Way == "1")
					{
						cout << "Введите название файла для создания." << endl;
							cin >> Way;
						while (true)
						{
							cout << "Создать пустым?(y/n)" << endl;
							cin >> Answer;
							if (Answer == "y")
							{
								if (creat(Way, 0) == 0)
								{
									cout << "Файл был успешно создан." << endl;
										break;
								}
								else break;
							}
							else if (Answer == "n")
							{
								if (creat(Way, 1) == 0)
								{
									cout << "Файл был успешно создан." << endl;
										break;
								}
							}
							else
								cout << "Неверный ввод команды." << endl;
						}
					}
					else if (Way == "2")
					{
						cout << "Введите название файла (с расширением) для редактирования." << endl;
							cin >> Way;
						write(Way);
					}
					else if (Way == "3")
					{
						cout << "Введите название файла (с расширением) для просмотра." << endl;
							cin >> Way;
						read(Way);
					}
					else if (Way == "4")
					{
						cout << "Введите название файла (с расширением) для удаления." << endl;
							cin >> Way;
						Remove(Way, 2);
					}
					else if (Way == "5")
					{
						if (Way == "exit")
							cout << " Выход в меню." << endl;
							break;
					}
					else
						cout << "Неверный ввод команды (Введите цифры из предоставленных)" << endl;
				}
			}
			else if (Answer == "2")
			{
				if (T == 0)
				{
					cout << "Введите название папки для перехода." << endl;
						cin >> Way;
					Travel(Way, 0);
				}
				else
				{
					cout << "Вернуться в каталог выше? (y/n)" << endl;
					cin >> Way;
					if (Way == "y")
					{
						Way = Trans(Way, 3);
						Travel(Way, 1);
					}
					else if (Way == "n")
					{
						cout << "Введите название папки для перехода." << endl;
							cin >> Way;
						Travel(Way, 0);
					}
					else
					{
						cout << "Неверный ввод команды." << endl;
					}
				}
			}
			else if (Answer == "3")
			{
				cout << "Завершение работы." << endl;
				Journal(Use, 1);
				system("pause");
				return 0;
			}
			else
				cout << "Неверный ввод команды. (Введите цифры из предоставленных)" << endl;
		}
	}
}
