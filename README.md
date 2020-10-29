

// PROJECT = Bank management system
#include<stdio.h>
#include<stdlib.h>
#include <string.h>
#include <conio.h>
void main()
{
     int  option,y,m,d,bal,w,b,t,am,x=0,ym=0,z=0;
     char name[15],ac[20]="",xx[20]="",rc[20]="",da[20]="",na[10]; 
     FILE *fp;
     FILE *ft;
             printf("\n\n");    
             printf("\t\t\t\t* * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * *\n");
             printf("\t\t\t\t*                  =====================                      *\n");
             printf("\t\t\t\t*                  welcome to world bank                      *\n");
             printf("\t\t\t\t*                  =====================                      *\n");
             printf("\t\t\t\t* * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * *\n");
        //to create new account..
             printf("\n\n\nPress 1. To create a new account \nPress 2. To access  existing account \n");
             scanf("%d",&y);
      while(1)
             {
               if(y==1)
                  {
                       printf("\nEnter the account number to create a account : ");
                       scanf("%s",&xx);
                       printf("\nenter name of account holder : ");
                       scanf("%s",&na);
                      
                       fp=fopen(xx,"w");
                        if(fp==NULL)
                             {
                               printf("\n!!!Account not created!!!\n");
                             }
                            
                          else{   printf("\n\n****   Account successfuly  created  ****\n\n");
                                  printf("\nEnter the amount to make first transaction : ");
                                  scanf("%d",&m);                   
                                  fprintf(fp,"%d",m);
                                  printf("\nAmount have been deposited succsessfuly\n");
                                  
                          }
                       fclose(fp);
                       printf("Do you want to create another account \n1.yes     2.no ");
                      scanf("%d",&y);
                  }   
                       else {
                           break;
                       }   
            }
                system("cls");
               // to work on exsisting account..
          printf("\t\t\4 * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * \4\n");
          printf("\t\t   *                                                         *\n");
          printf("\t\t   *     \5\5  You can access existing acount   \5\5             *\n");
          printf("\t\t   *                                                         *\n");
          printf("\t\t\4 * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * \4\n");
           while(1) {     
                   printf("\n\nEnter your name: ");
                   scanf("%s",&name[15]);
                   
                   printf("\nPlease enter your account number  : ");
                   scanf("%s",&ac);
              fp=fopen(ac,"r");
              if(fp==NULL)
              { printf("\n\n****** Account not matched *******\n\n");
                printf("            TRY AGAIN\n                ");
              continue;
              }
              else{ printf("\n\n****** Account matched *******\n\n");
                    break;
                   }
              fclose(fp);  
           }
              
          do
            {  
              printf("\n\t\t\tChoose what you want to do :\n");
              printf("\t\t\t1 - Check balance\n");
              printf("\t\t\t2 - Deposit money\n");
              printf("\t\t\t3 - Withdraw money\n");
              printf("\t\t\t4 - Transfer money\n");
              printf("\t\t\t5 - Exit\n");
              scanf("%d",&option);
                      switch(option)
                                  {  
                                      case 1:{  
                                                 fp=fopen(ac,"r");
                                                 fscanf(fp,"%d",&b);
                                                 printf("     \n\n\n  Your balance is: %d\n ",b);
                                                fclose(fp); 
                                                getch();
                                                system("cls");
                                                break;        
                                              }
                                       case 2:{  fp=fopen(ac,"r");
                                                    fscanf(fp,"%d",&bal);
                                                    printf("\nEnter amount to deposit:");
                                                    scanf("%d",&d);
                                                    x=x+d;
                                                    bal=bal+d;
                                                    fclose(fp);
                                                    fp=fopen(ac,"w");
                                                    fprintf(fp,"%d",bal);
                                                    fclose(fp);
                                                    printf("\nAmount has been deposited successfuly\n");
                                                    fp=fopen(ac,"r");
                                                      fscanf(fp,"%d",&bal);
                                                      printf("\nYour balance is : %d",bal);
                                                    fclose(fp);
                                                     getch();
                                                     system("cls");
                                                          break;
                                              }
                                        case 3:{       fp=fopen(ac,"r");
                                                       fscanf(fp,"%d",&bal);
                                                       fclose(fp);
                                                       printf("\nEnter amount to withdrawal:");
                                                       scanf("%d",&w);
                                                       if(bal>=w)
                                                       {
                                                         ym=ym+w;
                                                       bal=bal-w;
                                                      fp=fopen(ac,"w");
                                                       fprintf(fp,"%d",bal);
                                                       fclose(fp);
                                                       printf("\nAmount has been withdrawal successfuly\n");
                                                      fp=fopen(ac,"r");
                                                      fscanf(fp,"%d",&bal);
                                                      printf("\nYour balance is : %d",bal);
                                                      fclose(fp);
                                                       }
                                                       else
                                                       {
                                                         printf("\n\nInsuficent balance please try again\n");
                                                       }
                                                        getch();
                                                        system("cls");
                                                      
                                                       break;
                                                  }
                                            case 4: {  
                                                      fp=fopen(ac,"r");
                                                       fscanf(fp,"%d",&bal);
                                                       printf("\nEnter amount to transfer:");
                                                       scanf("%d",&t);
                                                       printf("\n Enter the reciver account:\n");
                                                       scanf("%s",&rc);
                                                       if(bal>=t)
                                                       { z=z+t;
                                                       bal=bal-t;
                                                    ft=fopen(rc,"r");
                                                    fscanf(ft,"%d",&am);
                                                    am=am+t;
                                                   fclose(ft);
                                                    ft=fopen(rc,"w");
                                                    fprintf(ft,"%d",am);
                                                    fclose(ft);
                                                    fclose(fp);
                                                     fp=fopen(ac,"w");
                                                       fprintf(fp,"%d",bal);
                                                       fclose(fp);
                                                       printf("\nAmount has been transfer successfuly\n");
                                                        fp=fopen(ac,"r");
                                                      fscanf(fp,"%d",&bal);
                                                      printf("\nYour balance is : %d",bal);
                                                    fclose(fp);
                                                     }
                                                       else
                                                       {
                                                         printf("\n\nInsuficent balance please try again\n");
                                                       }
                                                        getch();
                                                        system("cls");
                                                      break;
                                                }                 
                                                 case 5:{   break;               }
                                                 default:{ printf("\nWrong input\n"); }
                                          }
                                         
                           }while(option!=5);
                           fp=fopen(ac,"r");
                           fscanf(fp,"%d",&b);
                   printf("\n\n");  
             printf("\t\t\t\2 \2 \2 \6 \6 \6 \6 \6 \6 \6 \6 \6 \6 \6 \6 \6 \6 \6 \6 \6 \6 \6 \6 \6 \6 \6 \6 \6 \6 \6 \6 \6 \6 \6 \6 \6 \2 \2 \2\n");      
                   printf("\t\t\t      \6                 Net balance : Rs %d                         \6\n",b); 
                   printf("\t\t\t      \6                 Total amount deposited : Rs %d                 \6\n",x); 
                   printf("\t\t\t      \6                 Total amount withdrawal : Rs %d                \6\n",ym); 
                   printf("\t\t\t      \6                 Total amount transfer : Rs %d                  \6\n",z);
         printf("\t\t\t\2 \2 \2 \6 \6 \6 \6 \6 \6 \6 \6 \6 \6 \6 \6 \6 \6 \6 \6 \6 \6 \6 \6 \6 \6 \6 \6 \6 \6 \6 \6 \6 \6 \6 \6 \6 \2 \2 \2\n");     
                   fclose(fp);
                   getch();    
}

