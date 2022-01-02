// # Beam-defelction
//c program to calculate beam deflection depending of support types and applied loading. Language:Latvian

/**********************************************************************
* Izlieces aprēķins sijai atkarībā no balstījuma un slogojumam veida. *
* Izmantotie apzīmējumi un to mērvienības:                            *
* q   => slodze (kN/m vai kN)                                         *
* L   => laidums (cm)                                                 *
* E   => elastības modulis (kN/cm^2)                                  *
* I   => inerces moments (cm^4)                                       *
* u   => izliece (cm)                                                 *
**********************************************************************/
#include <stdio.h>                                                                                  //ievades, izvades funkcijas
#include<math.h>                                                                                    // matemātiskās funkcijas

int main()                                                                                          //galvenā funkcija
{                                                                                                   //funkcijas ķermeņa sākums
    char izvele;                                                                                    //lokālie mainīgie (veseli skaitļi)
    float q,L,E,u,I;                                                                                //lokālie mainīgie (reālie skaitļi)
    int veids;                                                                                      //lokālie mainīgie (veseli skaitļi)
    do {                                                                                            //cikls ar pārbaudi cikla beigās pēc nosacījuma
    printf("Ievadiet sijas materiāla elastības moduli E (kN/cm^2) un inerces momentu I(cm^4):\n");  //teksta izvade un \n pārceļ kursoru jaunā rindā
    scanf("%f %f",&E,&I);                                                                           //nolasa mainīgos un piešķir vērtības
    printf("Ievadiet sijas laidumu: L(cm):");                                                       //teksta izvade
    scanf("%f",&L);                                                                                 //nolasa mainīgos un piešķir vērtības
    printf("\n Izvēlieties atbisltošo sijas balstījuma un slogojuma veidu:\n");                     //teksta izvade
        printf(" 1 - divbalstu sija, koncentrēta slodze\n");                                        //teksta izvade
        printf(" 2 - divbalstu sija, vienmērīgi izkliedēta slodze\n");                              //teksta izvade
        printf(" 3 - konsolsija, koncentrēta slodze galā\n");                                       //teksta izvade
        printf(" 4 - konsolsija, vienmērīgi izkliedēta slodze\n");                                  //teksta izvade
        printf(" Izvēlieties atbisltošo veidu (1 līdz 4): ");                                       //teksta izvade
        scanf("%d", &veids);                                                                        //nolasa mainīgos un piešķir vērtības
        switch(veids) {                                                                             //dod iespēju izvēlēties vienu no alternatīvām
          case 1: printf("\n Ievadiet koncentrēto slodzi P (kN): "); break;                         //iterācija ar teksta izvadi un pārtraukumu ar izeju no tās
          case 2: printf("\n Ievadiet izkliedēto slodzi q (kN/m): "); break;                        //iterācija ar teksta izvadi un pārtraukumu ar izeju no tās
          case 3: printf("\n Ievadiet koncentrēto slodzi P (kN): "); break;                         //iterācija ar teksta izvadi un pārtraukumu ar izeju no tās
          case 4: printf("\n Ievadiet izkliedēto slodzi q (kN/m): ");                               //iterācija ar teksta izvadi un pārtraukumu ar izeju no tās
        }                                                                                           //cikla robeža
    scanf("%f",&q);                                                                                 //nolasa mainīgos un piešķir vērtības
    switch(veids) {                                                                                 //dod iespēju izvēlēties vienu no alternatīvām
          case 1: u=q*0.01*pow(L,3)/(48*E*I);                                                       //iterācija ar formulu un pow funkciju, kas atgriež vērtību, ko iegūst argumentu base kāpinot pakāpē p
			      break;
          case 2: u=5*q*0.01*pow(L,4)/(384*E*I);                                                    //iterācija ar formulu un pow funkciju, kas atgriež vērtību, ko iegūst argumentu base kāpinot pakāpē p
			      break;
          case 3: u=q*0.01*pow(L,3)/(3*E*I);                                                        //iterācija ar formulu un pow funkciju, kas atgriež vērtību, ko iegūst argumentu base kāpinot pakāpē p
			      break;
          case 4: u=q*0.01*pow(L,4)/(8*E*I);                                                        //iterācija ar formulu un pow funkciju, kas atgriež vērtību, ko iegūst argumentu base kāpinot pakāpē p
        }
    printf("\n Sijas izliece (cm) = %.2f\n\n", u);                                                  //% norāda vietu un izvada skaitli ar 2 cipariem aiz komata
    printf(" Vai vēlieties atkārtot? (Y/N): ");                                                     //teksta izvade
    scanf("%s", &izvele);                                                                           //nolasa ievadīto simbolu
    } while (izvele=='y');                                                                          //cikla pārbaudes nosacījums
    printf("\n");                                                                                   //teksta izvade
    return 0;
}
