# rockclime
import java.util.Scanner;
 
 public class RockClimbing {

 static int C[][];
 static int A[][];

 
 static int min(int a, int b) {
 return (a < b) ? a : b;
 }

 
 static int calcDanger(int m, int n) {
 
 for (int x = 0; x < n + 2; x++) {
 A[0][x] = 0;
 }
 
 for (int i = 0; i < n; i++) {
 A[1][i + 1] = C[0][i];
 }
 // initialize the ends of the wall of A
for (int x = 0; x < m + 1; x++) {
 A[x][0] = A[x][n + 1] = 999999;
 
 }
 
 for (int i = 2; i < m + 1; i++) {
 for (int j = 1; j < n + 1; j++) {
 A[i][j] = C[i - 1][j - 1] + min(min(A[i - 1][j - 1], A[i - 1][j]), A[i - 1][j + 1]);

 



 }
 }
 System.out.println("The DP table is −");
 for (int i = 0; i < m + 1; i++) { 



 for (int j = 0; j < n + 2; j++) {
 System.out.print(A[i][j] + " ");
 }
 System.out.println();
 }
 int minIngex = 0;
 int minDanger = A[m][minIngex];
 



 for (int i = 1; i < n + 2; i++) {
 if (minDanger > A[m][i]) {
 minIngex = i;
 minDanger = A[m][i];
 }
 }
 return minIngex;
 }

 
 public static void main(String[] args) {
 
 int m, n;
 Scanner sc = new Scanner(System.in);
 System.out.println("No. of rows = ");
 m = sc.nextInt(); 

 System.out.println("No. of columns = ");
 n = sc.nextInt(); 
 C = new int[m][n];
 A = new int[m + 1][n + 2];
 
 for (int i = 0; i < m; i++) {
 for (int j = 0; j < n; j++) {
 C[i][j] = sc.nextInt();
 }
 }
 int x = calcDanger(m, n);
 System.out.println("Minimal danger = " + A[m][x]);
 }
}
