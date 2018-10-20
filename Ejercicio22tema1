#include <iostream>
#include <iomanip>
#include <windows.h>

using namespace std;

void ClearScreen(){
  HANDLE                     hStdOut;
  CONSOLE_SCREEN_BUFFER_INFO csbi;
  DWORD                      count;
  DWORD                      cellCount;
  COORD                      homeCoords = { 0, 0 };

  hStdOut = GetStdHandle( STD_OUTPUT_HANDLE );
  if (hStdOut == INVALID_HANDLE_VALUE) return;

  /* Get the number of cells in the current buffer */
  if (!GetConsoleScreenBufferInfo( hStdOut, &csbi )) return;
  cellCount = csbi.dwSize.X *csbi.dwSize.Y;

  /* Fill the entire buffer with spaces */
  if (!FillConsoleOutputCharacter(
    hStdOut,
    (TCHAR) ' ',
    cellCount,
    homeCoords,
    &count
    )) return;

  /* Fill the entire buffer with the current colors and attributes */
  if (!FillConsoleOutputAttribute(
    hStdOut,
    csbi.wAttributes,
    cellCount,
    homeCoords,
    &count
    )) return;

  /* Move the cursor home */
  SetConsoleCursorPosition( hStdOut, homeCoords );
  }

int lectura(){
	int a;
	cout << "Introduzca un numero: ";
	cin >> a;
	
	return a;
}

char menu(){
	char a;
	ClearScreen();
	cout << "Elige una de las siguientes operaciones:\n"
		 << "\tSumar (S)\n" << "\tRestar (R)\n" << "\tMultiplicar (M)\n" 
		 << "\tDividir (D)\n" << "\tCambiar operandos (C)\n" 
		 << "\tTerminar (T)\n";
	
	cin >> a;
	return a;
}

int main(void){
	
	int num1, num2;
	char comparador;
	double resultado;
	bool seguir = 1, operacion;
	
	num1 = lectura();
	num2 = lectura();
	
	while(seguir){
		comparador = menu();
		if(comparador == 'S'){
			resultado = num1 + num2;
			operacion = true;
		}else if(comparador == 'R'){
			resultado = num1 - num2;
			operacion = true;
		}else if(comparador == 'M'){
			resultado = num1 * num2;
			operacion = true;
		}else if(comparador == 'D'){
			resultado = num1 / num2;
			operacion = true;
		}else if(comparador == 'C'){
			num1 = lectura();
			num2 = lectura();
			operacion = false;
		}
		if (operacion){
			cout << "El resultado es: " << resultado << endl;
			cout << "Si desea terminar introduzca una (T): ";
			cin >> comparador;
		}
		if (comparador == 'T'){
			seguir = 0;
		}
	}	
}
