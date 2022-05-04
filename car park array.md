//Kaan Tapan


#include<stdio.h>

//print the parking place function
void parking_lot(int PL[10][10]) //take the arrey size
{
   int i,j;
   for(i=0;i<10;i++)
   {
       for(j=0;j<10;j++)
       printf("  %d",PL[i][j]);
    
	   printf(" \n");
		   
   }
  
}

// the car enter function
int enter_the_car(int PL[10][10], int ticket) //function for new car
{
   int i, j;
   for(i=0;i<10;i++)
   for(j=0;j<10;j++)
   if(PL[i][j]==-1)
   {
   PL[i][j]=ticket; //remove the -1 put the ticket number
   return 1;
   }
   return -1;
}

// Delete the car function
int delete_the_car(int PL[10][10],int ticket) //function for deleted car
{
   int i,j;
   for(i=9;i>=0;i--)
   for(j=9;j>=0;j--)
   if(PL[i][j]==ticket)
   {
       PL[i][j]=-1; //remove the ticket and put -1
       return 1;
   }
   return -1;
}


 int main()
{
   
   int PL[10][10], input;
   int i,j;
  
 
   for(i=0;i<10;i++)
   for(j=0;j<10;j++)
        PL[i][j]=-1;
  
  
   printf("Welcome");
   do 
   {    
       printf("\nPlease input your command:\n"); // input the command
       scanf("%d",&input);
       if(input==0) // command for ('0') print the lot and exit the code
       {
           printf("Goodbye. Here is the final parking lot\n");
		parking_lot(PL);
        
       }
       
	   else if(input==1) // command for ('1') show the table
       {
            printf("Parking Lot :\n"); 
		   parking_lot(PL);
       }
       
	   
	   else if(input==2) // command for ('2') Add the car
       {
           printf(" \nA new car is entering.Please input a ticket number:\n");
           scanf("%d",&input);
           if(enter_the_car(PL,input)==1){
		   
		   input=2;}
		   
       }
       
	   else if(input==3) // command for ('3') remove the car
       {
           printf("\nA car is leaving. Please input the ticket number of leaving car :\n");
           scanf("%d",&input);
           if(input==-1)
           {
               printf("\n Wrong ticket number !");
           }
           else if(delete_the_car(PL,input)==1){
           	input=3;
		   }
       }
       
	   else
       {
           printf("\nIncorrect command, new commend needed."); //control the correct command
       }
   }while(input!=0); 

}
