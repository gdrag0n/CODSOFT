```
import java.util.Scanner;  
import java.util.InputMismatchException; 


public class Marks   
{  
    
    public int num()
    {
        Scanner sc=new Scanner(System.in);
        Marks m=new Marks();
        
        try
        {
            System.out.print("Enter the number of subjects: ");
            return(sc.nextInt());
        }
        catch (InputMismatchException ex)
        {
            System.out.println("Invalid Input. Only integer inputs are accepted.");
            return m.num();
        }
    }

    public static void main(String[] args)   
    {  
        
        //initializing Scanner class
        Scanner sc=new Scanner(System.in);
        Marks m=new Marks();
        
        int len=m.num();


        //creates an array in the memory of length 10  
        int[] arr = new int[len];  
        
        System.out.println("Enter the elements of the array: ");  
        for(int i=0; i<len; i++)  
        {  
            //reading array elements from the user   
            arr[i]=sc.nextInt();  
        } 
        
        
        //total marks=sum of all subject marks
        int s=0;
        for (int i=0; i<len; i++)
        {  
            s=s+arr[i];  
        }
        
        
        
        //average percentage calculation
        //int len=arr.length;
        int avg=s/len;
        
        

        //grade determination
        String grade;
        if(avg>90)
        {
            grade = "A";
        }
        else if(90>=avg && avg>80)
        {
            grade = "B";
        }
        else if(80>=avg && avg>70)
        {
            grade = "C";
        }
        else if(70>=avg && avg>60)
        {
            grade = "D";
        }
        else if(60>=avg && avg>50)
        {
            grade = "E";
        }
        else
        {
            grade="F";
        }
        
        
        System.out.println("Sum of all scores is: "+s);
        System.out.println("Your average percentage is: "+avg+"%");
        System.out.println("You've earned grade "+ grade);

    }  
}
```
