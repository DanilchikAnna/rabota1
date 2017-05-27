# rabota1
#include "stdafx.h"
#include <stdio.h>
#include <stdlib.h>

int N;//количество конденсаторов
float *cond; // массив конденсаторов

int inputC(){ // функция ввода
	printf("Vvtdite kolichestvo kondensatorov: ");
	scanf("%d", &N);
	if (N <= 0){ // проверка, чтоб количество было больше 0
		printf("ploho\n");
		return 1; // код ошибки
	}
	cond = (float *)malloc(N * sizeof(float)); // выделение памяти массива под количество конденсаторов
	for (int i = 0; i < N; i++){ // цикл ввода емкостей
		printf("Vvedite emkost %d-go condensatora: ", i + 1);
		scanf ("%f", &cond[i]); // функция ввода
	}
	return 0; // нет ошибок
}

double calcSum (int N, float *cond){
	float temp = 0.0;
	for (int i = 0; i < N; i++){
		temp += 1 / cond[i]; //нахождение суммы ряда
	}
	return 1 / temp; //присвоение функции результата
}


int main(){
	if (inputC() == 0) {// Если нет ошибок ввода, то продолжай
		printf("\nSummarnaya emkost: %f\n", calcSum(N, cond)); // вывод результатов
	}
	free(cond); // очистка памяти
	system("pause"); // задержка экрана
	return 0;
}
