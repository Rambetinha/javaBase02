# javaMatriz01
package javaExercicioMatrizes01;

import java.util.Scanner;
import java.util.Locale;

public class ExercicioMatrizes01 {
	public static void main(String[] args) {
		Locale.setDefault(Locale.ENGLISH);
		Scanner sc = new Scanner(System.in);

		int N = sc.nextInt();
		double soma = 0;
		double[][] matriz = new double[N][N];
		double[][] matrizAlterada = new double[N][N];
		double[][] linhaMatriz = new double[N][N];
		double[][] colunaMatriz = new double[N][N];

		int x = 0;
		int volta = 0;
		int matriz_alterada = 0;
		int linha = 0;
		int coluna = 0;
		int mostrarMatriz = 0;

		for (int i = 0; i < N; i++) {
			for (int j = 0; j < N; j++) {
				matriz[i][j] = sc.nextDouble();

				// alterando valores negativos para valores positivos ao quadrado dentro da matriz 
				if (matriz[i][j] < 0) {
					matrizAlterada[i][j] = Math.pow(Math.abs(matriz[i][j]), 2);
					matriz_alterada += 1;
				}

				//somando valores positivos
				if (matriz[i][j] > 0) {
					soma += matriz[i][j];
				}
			}
		}
		System.out.println("ESCOLHA UMA LINHA: ");
		x = sc.nextInt();
		linha = x;

		System.out.println("ESCOLHA UMA COLUNA: ");
		x = sc.nextInt();
		coluna = x;

		//
		for (int i = 0; i < N; i++) {
			for (int j = 0; j < N; j++) {
			    //pegando a  linha escolida e posicionando dentro da variavel = linhaMatriz
				linhaMatriz[linha][j] = matriz[linha][j];
			    //pegando a  coluna escolida e posicionando dentro da variavel = colunaMatriz
				colunaMatriz[i][coluna] = matriz[i][coluna];
			}
		}

		System.out.print("SOMA DOS POSITIVOS: " + soma);
		System.out.println();

		for (int i = 0; i < N; i++) {
			for (int j = 0; j < N; j++) {
				if (volta == 0) {
					System.out.print("LINHA ESCOLIDA: ");
				}
				while (linhaMatriz[linha][j] != 0 && j < N) {
					System.out.print(linhaMatriz[linha][j] + " ");
					j += 1;

					if (j == N) {
						break;
					}
				}

				System.out.println();

				if (volta == 0) {
					System.out.print("COLUNA ESCOLIDA: ");
				}
				while (colunaMatriz[i][coluna] != 0 && i < N) {
					System.out.print(colunaMatriz[i][coluna] + " ");
					i += 1;
					if (i == N) {
						break;
					}
				}

				System.out.println();

			}
		}
		if (volta == 0) {
			System.out.print("DIAGONAL PRINCIPAL: ");
		}
		for (int i = 0; i < N; i++) {
			System.out.print(matriz[i][i] + " ");
		}

		System.out.println();

		// so vai ler se caso la em cima nao for digitado nenhum valor negativo
		for (int i = 0; i < N && matriz_alterada == 0; i++) {
			for (int j = 0; j < N; j++) {
				if (mostrarMatriz == 0) {
					System.out.println("MATRIZ: ");
					mostrarMatriz += 1;
				}
				System.out.print(matriz[i][j] + " ");
			}
			System.out.println();
		}

		// so vai ler se caso la em cima for digitado algum valor negativo
		for (int i = 0; i < N && matriz_alterada > 0; i++) {
			for (int j = 0; j < N; j++) {
				if (mostrarMatriz == 0) {
					System.out.println("MATRIZ ALTERADA: ");
					mostrarMatriz += 1;
				}
				if (matriz[i][j] < 0) {
					System.out.print(matrizAlterada[i][j] + " ");
				} else {
					System.out.print(matriz[i][j] + " ");
				}
			}
			System.out.println();
		}
	}

}
