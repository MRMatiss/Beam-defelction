// # Beam-deflection
//c program to calculate beam deflection depending of support types and applied loading.

/****************************************************************************
* Beam deflection calculation depending of support types and applied loading*
* Used variables and units:                     	                    *
* q   => load (kN/m or kN)                                                  *
* L   => length (cm)                                                        *
* E   => modulus of elasticity (kN/cm^2)                                    *
* I   => moment of inertia (cm^4)                                           *
* u   => deflection (cm)                                                    *
****************************************************************************/
#include <stdio.h>                                                                                  
#include<math.h>                                                                                    

int main()                                                                                          
{                                                                                                   
    char choice;                                                                                    
    float q,L,E,u,I;                                                                                
    int type;                                                                                      
    do {                                                                                            
    printf("Enter the beam material modulus of elasticity E (kN/cm^2)and moment of inertia I(cm^4):\n");  
    scanf("%f %f",&E,&I);                                                                           
    printf("Enter the legth of beam: L(cm):");                                                       
    scanf("%f",&L);                                                                                 
    printf("\n Choose the beam support type and loading:\n");                     
        printf(" 1 - two support beam, concentrated load at beam free end\n");                                        
        printf(" 2 - two support beam, uniformly distributed load\n");                             
        printf(" 3 - single support beam with free end, concentrated load at beam free end\n");                                       
        printf(" 4 - single support beam with free end, uniformly distributed load\n");                                  
        printf(" Choose the appropriate type (1 to 4): ");                                       
        scanf("%d", &type);                                                                        
        switch(type) {                                                                             
          case 1: printf("\n Ievadiet koncentrēto slodzi P (kN): "); break;                         
          case 2: printf("\n Ievadiet izkliedēto slodzi q (kN/m): "); break;                        
          case 3: printf("\n Ievadiet koncentrēto slodzi P (kN): "); break;                         
          case 4: printf("\n Ievadiet izkliedēto slodzi q (kN/m): ");                               
        }                                                                                          
    scanf("%f",&q);                                                                                 
    switch(type) {                                                                                 
          case 1: u=q*0.01*pow(L,3)/(48*E*I);                                                      
			      break;
          case 2: u=5*q*0.01*pow(L,4)/(384*E*I);                                                     
			      break;
          case 3: u=q*0.01*pow(L,3)/(3*E*I);                                                       
			      break;
          case 4: u=q*0.01*pow(L,4)/(8*E*I);                                                       
        }
    printf("\n Beam deflection (cm) = %.2f\n\n", u);                                                  
    printf(" Do You want to repeat? (Y/N): ");                                                     
    scanf("%s", &choice);                                                                           
    } while (choice=='y');                                                                          
    printf("\n");                                                                                   
    return 0;
}
