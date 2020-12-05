/*
PROGRAMMER: BABAJIDE SANUSI
DATE: 14 MAY 2020
PURPOSE: CSC126 -  Airline program that allows user to book seats or check if a seat as been booked
*/

//made as constants incase airline size increases
const int sROW = 13, sCOLUMN = 6;

#include <iostream>
#include <ctime>
#include <cstdlib>
#include <iomanip>
#include <string>

using namespace std;

void sepa();
void displayMap(int a[][sCOLUMN]);
void makeReservation(int a[][sCOLUMN], int&);


int main()
{
	cout << "Welcome to CSC126 airline!\n";
	int seats[sROW][sCOLUMN];
	int avSeats = 0;
	char sel = '1';
	srand(time(NULL));

	//assign seats randomly
	for (int i = 0; i < sROW; i++)
		for (int j = 0; j < sCOLUMN; j++)
		{
			seats[i][j] = rand() % 2;
			avSeats += seats[i][j];
		}
	
	cout << "Enter '1' to display a graphic image of the seats available." << endl;
	cout << "Enter '2' to book a seat" << endl;
	cin >> sel;

	while (sel != '1' && sel != '2')
	{
		cout << "Please enter valid number: ";
		cin >> sel;
	}

	sepa();

	if (sel == '1')
	{
		displayMap(seats);
		cout << endl << endl;
		sel++; //Ask if the user wants a seat
	}

	if (sel == '2')
		makeReservation(seats, avSeats);
	

	cout << "\nThank you for visiting our website.\nVisit us again to book another seat\n";

	system("pause");
	return 0;
}

void sepa()
{
	for(int i = 0; i < 2; i++)
		cout << endl << setfill('*') << setw(55) << '*';

	cout << endl << endl << setfill(' ');
}

void displayMap(int a[][sCOLUMN])
{
	char cha = 'A';

	//List to print * or X
	char xst[2] = { 'X', '*' }; 

	//Print outer row
	cout << setw(6) << ' ' << '|';
	for (int i = 0; i < sCOLUMN ; i++)
		cout << setw(6) << static_cast<char>(cha + i);
	cout << endl;


	//print seats
	for (int i = 0; i < sROW; i++)
	{
		cout << "Row " << setw(2) << i + 1 << '|';
		for (int j = 0; j < sCOLUMN; j++)
			cout << setw(6) << right << xst[a[i][j]];
		cout << endl;
	}


	cout << endl;
	cout << "X = Booked";
}

void makeReservation(int a[][sCOLUMN], int &seats)
{
	cout << endl;

	int row = 7;
	char anot = '0';

	//Char to separate input
	char column = 'C';

	cout << "Hi customer, we have " << seats << " seats available." << endl;
	cout << "We have " << sROW << " rows and " << sCOLUMN <<" seats (A-" << static_cast<char>('A'+sCOLUMN-1) <<") on each row totaling "<< sCOLUMN * sROW <<" seats\n";
	cout << "Enter the seat number you would like to select in the format below." << endl;
	cout << "'ROW''COLUMN' (ex. 1D) " << endl;

	cin >> row >> column;
	column = toupper(column);

	while (row < 1 || row > sROW || column < 'A' || column > 'A' + sCOLUMN-1)
	{
		cout << "Please enter a valid input." << endl;
		cin >> row  >> column;
		column = toupper(column);
	}


	//adjustments to make rows and columns match 
	//cin of column is the ascii value. it is converted to the index of the array.
	column -= 65;
	row--;


	//confirm reservation
	if (a[row][column] == 1)
	{
		cout << "Reservation has successfully been made!";
		a[row][column] = 0;
		seats--;

		sepa();

		cout << endl << "MAP UPDATED!" << endl;
		displayMap(a);
		
	}
	else
		cout << "Sorry, the seat has been booked.";


	sepa();
	cout << "\nWould you like to book a seat?\n";
	cout << "Enter '0' for YES and '1' for NO\n";
	cin >> anot;

	while (anot != '0' && anot != '1')
	{
		cout << "Please enter valid number: ";
		cin >> anot;
	}

	while (anot == '0')
		makeReservation(a, seats);

	cout << endl;
	while (anot == '1')
		break;
}
