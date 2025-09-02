import java.util.Scanner;

public class Ejer12Matriz {


    public static void main(String[] args) {
        int[][] matriz = crearMatriz();

        if (matriz == null) {
            System.out.println("No se puede realizar la matriz.");
            return;
        }

        System.out.println("\nMatriz original:");
        mostrarMatriz(matriz);

        procesarMatriz(matriz);

        System.out.println("\nMatriz final:");
        mostrarMatriz(matriz);
    }

    // Módulo crear y cargar matriz
    public static int[][] crearMatriz() {
        Scanner scanner = new Scanner(System.in);
        System.out.print("Ingrese el tamaño de la matriz cuadrada (n): ");
        int n = scanner.nextInt();

        if (n <= 0) {
            System.out.println("El tamaño debe ser un número positivo.");
            scanner.close();
            return null;
        }

        int[][] matriz = new int[n][n];
        System.out.println("Ingrese los valores de la matriz:");
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n; j++) {
                System.out.print("Matriz[" + i + "][" + j + "]: ");
                matriz[i][j] = scanner.nextInt();
            }
        }
        scanner.close();
        return matriz;
    }

    // Módulo recorrer la Matriz 
    public static void procesarMatriz(int[][] matriz) {
        int n = matriz.length;

        for (int j = 0; j < n; j++) {
            int indiceMaximo = j;
        
            for (int i = j + 1; i < n; i++) {
                if (Math.abs(matriz[i][j]) > Math.abs(matriz[indiceMaximo][j])) {
                    indiceMaximo = i;
                }
            }
            

            int[] temp = matriz[j];
            matriz[j] = matriz[indiceMaximo];
            matriz[indiceMaximo] = temp;

            // Rellenar con ceros a la derecha de la diagonal
            for (int k = j + 1; k < n; k++) {
                matriz[j][k] = 0;
            }
        }
    }
    
    // Módulo para mostrar la matriz 
    public static void mostrarMatriz(int[][] matriz) {
        for (int i = 0; i < matriz.length; i++) {
            for (int j = 0; j < matriz[i].length; j++) {
                System.out.printf("%6d", matriz[i][j]);
            }
            System.out.println();
        }
    }
}
