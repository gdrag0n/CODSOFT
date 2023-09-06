# Number Game
### Classes
- Scanner
- Random
- InputMismatchException

### Functions
- rand: Generates a random integer within the decided range
- guess: Makes user guess the random number generated
- comp: Compares the guessed value with the random number
- ans: Deals with extra tries
- mainmain: Significant structure carrying all above functions to perform the required task
  
```
import java.util.Scanner;
import java.util.Random;
import java.util.InputMismatchException; 

public class RandomNo
{
//F0
//random number generator method
    public int rand(int l, int u)
    {
        Random rand = new Random();
        int r = rand.nextInt(u-l+1) + l;
        return r;
    }
    
//F1
//User guess
    public int guess()
    {
        //initializing Scanner
        Scanner sc = new Scanner(System.in);

        
        try 
        {  
            System.out.println("Guess the number: ");  
            Integer a = sc.nextInt();
            return(a);  
        }   
        catch (InputMismatchException ex) 
        {  
            System.out.println("Invalid input. Please enter a valid integer.");
            RandomNo rn = new RandomNo();
            return(rn.guess());
        }  
    }    

//F2
//Compare
    public String comp(int s, int r, int g)
    {
        //comparison
        if(r==g)
        {
            return("Hooray! Your score is "+s);
        }
        else
        {
            return("");
        }
    }

//F3
    public String ans(int i, int r)
    {   
        int s=0;
        int guess=guess();
        String res=comp(s,r,guess);
            
        if(!res.isEmpty())
        {
            return(res);
        }
        else if(i==0)
        {
            return("You are out of tries. Game Over.");
        }
        else
        {
            int tries=i-1;
            System.out.println(tries+" more tries left!");
            
            RandomNo rn = new RandomNo();
            return(rn.ans(i-1,r));
        }
    }
    

//F4
    public String mainmain()
    {
        //initializing Scanner
        Scanner sc = new Scanner(System.in);
     
        //guess
        //System.out.print("Lower limit: ");
        //int l = sc.nextInt();
        
        //System.out.print("Upper limit: ");
        //int u = sc.nextInt();
        
        int l=0;
        int u=100;
        
        //
        int r=rand(l,u);
        
        //to test for the correct response
        //System.out.println(r);
        

        int i=0;
        int s=10;
        
        while(i<10)
        {   
            s--;
            int g=guess();
            String res=comp(s+1,r,g);
            
            if(res.isEmpty())
            {
                System.out.println("Hm, let's try again");
                i++;
            }
            else
            {
                return(res);      
            }
        }
        
        System.out.println("Uh-Oh. You are out of score attempts.");
        System.out.println("If you'd like yet another try, type 'try' and if you'd like to reset the game, type 'reset': ");
        //Scanner has already been initialized
        String inp = sc.nextLine();
        
        if(inp.equals("reset"))
        {
            return("Game has been reset. Game Over.");
        }
        else if(inp.equals("try"))
        {
            int t=10;
            
            RandomNo rn = new RandomNo();
            return(rn.ans(t,r));
        }
        else
        {
            return("Invalid input. Game Over.");
        }
    }



    public static void main(String args[])
    {
        RandomNo instance = new RandomNo(); 
        //Create an instance of the class
        String result=instance.mainmain();
        System.out.println(result);
    }

}

```

