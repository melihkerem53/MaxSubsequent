#include <stdio.h>
#include <time.h>
#include <stdlib.h>

#define BOYUT 100


int main() 
{
	int dizi[BOYUT] =
	{
  3883, 5301, -6544, -897, -8538, 8463, 8925, -5567, 2492, 6614,
  9153, -3808, -545, 7751, 463, -6964, -1888, 2822, -1087, 7041,
  4482, -2057, 1981, 9103, 9077, -2811, 7127, -9914, -90, 1322,
  2227, -1300, 1656, -8121, 4262, -8673, 7318, -7535, -6238, -889,
  8741, -3430, -473, -1433, -196, -4141, 907, 929, 5465, -9799,
  6908, 3128, 1151, -2058, 2072, 6228, -8370, -4080, -2829, 7058,
  3189, -153, 4993, 7204, 9277, -2167, 9929, -8766, 4835, 4657,
  8227, -1448, -1302, -6705, 7901, -2048, -3382, 710, -2411, -1429,
  -3802, -5874, -7062, -2204, 5371, 9005, -743, -6671, -2855, -1728,
  2224, 2681, 1535, -4571, 8387, 7003, -8970, 4512, -409, 3850 
	};

	int max_ardisik_toplam = dizi[0];
	int suanki_ardisik_toplam = dizi[0];
	int baslangic_index = 0;
	int bitis_index = 0;
	int suanki_baslangic_index = 0;

	for (int i = 1; i < BOYUT; i++)
	{
		if (dizi[i] > suanki_ardisik_toplam + dizi[i])
		{
			suanki_ardisik_toplam = dizi[i];
			suanki_baslangic_index = i;
		}
		else 
		{
			suanki_ardisik_toplam += dizi[i];
		}

		if (suanki_ardisik_toplam > max_ardisik_toplam) 
		{
			max_ardisik_toplam = suanki_ardisik_toplam;
			baslangic_index = suanki_baslangic_index;
			bitis_index = i;
		}
	}

	printf("En buyuk ardisik toplam: %d\n\n", max_ardisik_toplam);
	
	
	for(int i=0;i<BOYUT;i++)
	{
		if (i >= baslangic_index && i <= bitis_index)
		{
			printf("\033[31m%d\033[0m ", dizi[i]);
		}

		else
			printf("%d ", dizi[i]);

		if ((i +1)%10 == 0)
			printf("\n");
	}
	printf("\n");
	

	return 0;
}

