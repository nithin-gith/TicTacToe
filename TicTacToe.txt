import java.util.Scanner;

public class TicTacToe{
    static String[][] board = new String[3][3];
    static Scanner scan = new Scanner (System.in);
    static int row_no;
    static int col_no;
    static boolean avail;
    static boolean notValid;

    public static void main(String[] args) {
        System.out.println("\n\nLet's play tic-tac-toe");
        for (int i=0;i<3;i++){
            for (int j=0;j<3;j++){
                board[i][j] = "_";
            }
        }
        printBoard();
        for(int k = 0;k<9;k++){
            if (k%2==0){ //X-turn
                System.out.println("\n======\nX turn:\n======\n");
                System.out.print("Enter Row No:");
                row_no= scan.nextInt()-1;
                System.out.print("Enter Column No:");
                col_no= scan.nextInt()-1;
                notValid = notValid();
                if (notValid){
                    makingValidNumbers();
                }
                avail = checkAvail(row_no,col_no);
                if(avail){
                    board[row_no][col_no] = "X";
                    checkStatus();
                }
                
                else{ 
                    while(true){
                        System.out.println("\nPlease choose different row and column numbers!\n");
                        System.out.print("Enter Row No:");
                        row_no= scan.nextInt()-1;
                        System.out.print("Enter Column No:");
                        col_no= scan.nextInt()-1;
                        notValid = notValid();
                        if (notValid){
                            makingValidNumbers();
                        }
                        avail = checkAvail(row_no,col_no);
                        if(avail){
                            board[row_no][col_no]="X";
                            checkStatus();
                            break;
                        }
                    }    
                }
                printBoard();
            }
            else { //O-turn
                System.out.println("\n======\nO turn:\n======\n");
                System.out.print("Enter Row No:");
                row_no= scan.nextInt()-1;
                System.out.print("Enter Column No:");
                col_no= scan.nextInt()-1;
                notValid = notValid();
                if (notValid){
                    makingValidNumbers();
                }
                avail = checkAvail(row_no,col_no);
                if(avail){
                    board[row_no][col_no] = "O";
                    checkStatus();
                }
                
                else{ 
                    while(true){
                        System.out.println("\nPlease choose different row and column numbers!\n");
                        System.out.print("Enter Row No:");
                        row_no= scan.nextInt()-1;
                        System.out.print("Enter Column No:");
                        col_no= scan.nextInt()-1;
                        notValid = notValid();
                        if (notValid){
                            makingValidNumbers();
                        }
                        avail = checkAvail(row_no,col_no);
                        if(avail){
                            board[row_no][col_no]="O";
                            checkStatus();
                            break;
                        }
                    }    
                }
                printBoard();
            }
            }
            System.out.println("\n============\nIT'S A TIE!\n============\n");
        }
        
    


    public static void printBoard(){
        for (int i=0;i<3;i++){
            System.out.println("\t\n");
            for (int j=0;j<3;j++){
                System.out.print(board[i][j]+"  ");
            }
            System.out.println();
        }
        System.out.println("\n");
    }
    public static boolean checkAvail(int row_no,int col_no){
        if (board[row_no][col_no].equals("_")){
            return true;
        }
        else{
            return false;
        }
    }
    public static void checkStatus(){
        for(int i=0;i<3;i++){
            if(board[i][0]=="X"&&board[i][1]=="X"&&board[i][2]=="X"){
            System.out.println("=======\nX Win!\n=======");
            System.exit(0);
            }
            else if(board[0][i]=="X"&&board[1][i]=="X"&&board[2][i]=="X"){
                System.out.println("=======\nX Win!\n=======");
                System.exit(0);
            }
        }
        if((board[0][0]=="X"&&board[0][0].equals(board[1][1])&&board[0][0].equals(board[2][2])) || (board[0][2]=="X"&&board[0][2].equals(board[1][1])&&board[0][2].equals(board[2][0]))){
            System.out.println("=======\nX Win!\n=======");
            System.exit(0);
        }
        for(int i=0;i<3;i++){
            if(board[i][0]=="O"&&board[i][1]=="O"&&board[i][2]=="O"){
                printBoard();
                System.out.println("=======\nO Win!\n=======");
                System.exit(0);
            }
            else if(board[0][i]=="O"&&board[1][i]=="O"&&board[2][i]=="O"){
                printBoard();
                System.out.println("=======\nO Win!\n=======");
                System.exit(0);
            }
        }
        if((board[0][0]=="O"&&board[0][0].equals(board[1][1])&&board[0][0].equals(board[2][2])) || (board[0][2]=="O"&&board[0][2].equals(board[1][1])&&board[0][2].equals(board[2][0]))){
            System.out.println("=======\nO Win!\n=======");
            System.exit(0);
        }
           
    }
    public static boolean notValid(){
        if (row_no>2||row_no<0||col_no>2||col_no<0){
            return true;
        }
        else{
            return false;
        }
    }
    public static void makingValidNumbers(){
        while(true){
            System.out.println("\nPlease choose valid row and column numbers!\n");
            System.out.print("Enter Row No:");
            row_no= scan.nextInt()-1;
            System.out.print("Enter Column No:");
            col_no= scan.nextInt()-1;
            if(!notValid()){
            return;
            }
        }  
    }
}