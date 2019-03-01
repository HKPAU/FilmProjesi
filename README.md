# FilmProjesi
#include<stdio.h>
#include<stdlib.h>
#include<conio.h>
#include<string.h>



struct proje{
	char filmadi[100];
	char filmsenarist[100];
	char filmoyuncu[100];
	char filmyonetmen[100];
	char filmyil[100];
};

int main(){
	
	int secim;
	
	while(1){
	
	
	printf("1.Film eklemek icin seciniz.\n");
	printf("2.Film aramak icin tiklayin.\n");
	printf("3.Film listelemek icin tiklayin.\n");
	printf("4.Film güncellemek icin tiklayin.\n");
	printf("5.Film silmek icin tiklayin.\n");
	printf("6.Cikis yapmak icin tiklayiniz.\n");
	scanf("%d",&secim);
	
	if(secim==1){
		
		typedef proje film;
		
		film flm;
		FILE *fp = fopen("Filmler.txt","a");
		
		printf("Eklemek istediginiz filmin adini giriniz:");
		scanf("%s",flm.filmadi);
		printf("Eklemek istediginiz filmin senaristini giriniz:");
		scanf("%s",flm.filmsenarist);
		printf("Eklemek istediginiz filmin basrol oyuncusunu giriniz:");
		scanf("%s",flm.filmoyuncu);
		printf("Eklemek istediginiz filmin yonetmenini giriniz:");
		scanf("%s",flm.filmyonetmen);
		printf("Eklemek istediginiz filmin cikis yilini giriniz:");
		scanf("%s",&flm.filmyil);
		
		fprintf(fp,"%s %s %s %s %s\n",flm.filmadi,flm.filmsenarist,flm.filmoyuncu,flm.filmyonetmen,flm.filmyil);
		printf("Istediginiz film basariyla eklenmistir...\n");
		fclose(fp);
		
		_getch();
		
	}
	if(secim==2){
		printf("Arama menusune hosgeldiniz.");
		
		typedef proje film;
		film flm;
		
		char aranan[15];
		int arama;
		
		printf("Hangi sekilde arama yapacaksınız?\n");
		printf("1.Filmin adına gore\n");
		printf("2.Filmin yonetmenine gore\n");
		printf("3.Filmin senaristine gore\n");
		printf("4.Filmin oyuncusuna gore\n");
		printf("5.Filmin yilina gore\n");
		scanf("%d",&arama);
		
		if(secim==1){
			
			typedef proje film;
			film flm;
			char aranan[15];
			
			FILE *fp4 =fopen("Filmler.txt","r");
			
			if(fp4==NULL){printf("Aradiginiz film bulunamadı");}		//Eger ki film listede yoksa NULL döndürecek ve hata emsajını vericek... 
			
			printf("Aramak istediginiz filmin adini giriniz:");
			scanf("%s",aranan);
			
			while(!feof(fp4)){
				fscanf(fp4,"%s %s %s %s %d",flm.filmadi);
				if(strcmp(aranan,flm.filmadi)==0){
					printf("%s %s %s %s %d",flm.filmadi);
				}
			}
			
		fclose(fp4);
		_getch();	
			
		}
		else if(secim==2){
		typedef proje film;
		film flm;
		
			char aranan[15];
			
			FILE *fp5 =fopen("Filmler.txt","r");
			
			if(fp5==NULL){printf("Aradiginiz film bulunamadı");}
			
			printf("Aramak istediginiz filmin yonetmenini giriniz:");
			scanf("%s",aranan);
			printf("\nADI:%s ",flm.filmadi);
			
			while(!feof(fp5)){
				fscanf(fp5,"%s %s %s %s %d",flm.filmyonetmen);
				if(strcmp(aranan,flm.filmyonetmen)==0){
					printf("%5s %5s %5s %5s %d",flm.filmadi);
				}
			}
			
		fclose(fp5);
		_getch();	
		}
		
		else if(secim==3){
			typedef proje film;
		film flm;
		
			char aranan[15];
			
			FILE *fp6 =fopen("Filmler.txt","r");
			
			if(fp6==NULL){printf("Aradiginiz film bulunamadı");}
			
			printf("Aramak istediginiz filmin senaristini giriniz:");
			scanf("%s",aranan);
			printf("\nADI  \t  YONETMEN  SENARIST  \tBASROL      YIL");
			
			while(!feof(fp6)){
				fscanf(fp6,"%s %s %s %s %d",flm.filmsenarist);
				if(strcmp(aranan,flm.filmsenarist)==0){
					printf("%5s %5s %5s %5s %d",flm.filmadi);
				}
			}
			
		fclose(fp6);
		_getch();	
		}
		else if(secim==4){
		
		typedef proje film;
		film flm;
		
			char aranan[15];
			
			FILE *fp7 =fopen("Filmler.txt","r");
			
			if(fp7==NULL){printf("Aradiginiz film bulunamadı");}
			
			printf("Aramak istediginiz filmin basrol oyuncusunu giriniz:");
			scanf("%s",aranan);
			printf("\nADI");
			
			while(!feof(fp7)){
				fscanf(fp7,"%s %s %s %s %d",flm.filmoyuncu);
				if(strcmp(aranan,flm.filmoyuncu)==0){
					printf("%5s %5s %5s %5s %d",flm.filmadi);
				}
			}
			
		fclose(fp7);
		_getch();	
		}
		
		else if(secim==5){
			typedef proje film;
		film flm;
		
			char aranan[15];
			
			FILE *fp8 =fopen("Filmler.txt","r");
			
			if(fp8==NULL){printf("Aradiginiz film bulunamadı");}
			
			printf("Aramak istediginiz filmin yilini giriniz:");
			scanf("%s",aranan);
			printf("\nADI");
			
			while(!feof(fp8)){
				fscanf(fp8,"%s %s %s %s %s",flm.filmyil);
				if(strcmp(aranan,flm.filmyil)==0){
					printf("%5s %5s %5s %5s %5s",flm.filmadi);
				}
			}
			
		fclose(fp8);
		_getch();	
		}
		
	}
	
	if(secim==3){
		
		typedef proje film;
		film flm[50];
		
		printf("Listeleme menusune hosgeldiniz...");
		
		FILE *fp1 = fopen("Filmler.txt","r");
		if(fp1==NULL) 
		printf("Dosya Bulunamadi");
		
		int i,j=0,next=0,sayac1=0,sayac2=0,filmsayaci=0;;
		 
	
		
		while(!feof(fp1)){
			
			fscanf(fp1,"\n%s %s %s %s %s\n",flm[sayac1].filmadi,flm[sayac1].filmyonetmen,flm[sayac1].filmsenarist,flm[sayac1].filmoyuncu,flm[sayac1].filmyil);
			sayac1++;
			filmsayaci++;
		}
		
		char temp1[filmsayaci],temp2[filmsayaci],temp3[50];
		while(sayac1>0){
			
			while(sayac2<sayac1+j){
				
				for(i=0;i<filmsayaci;i++){
					 temp1[i]=flm[next].filmyil[i];
		         	 temp2[i]=flm[sayac2+1].filmyil[i];
				}
				if(strcmp(temp2,temp1)>0){
					
				 strcpy(temp3,flm[next].filmyil);
				 strcpy(flm[next].filmyil,flm[sayac2+1].filmyil);
		         strcpy(flm[sayac2+1].filmyil,temp3);
		         
		         strcpy(temp3,flm[next].filmadi);									//Burada listedeki tüm filmleri karşılaştırmak için kodları yazıyoruz....
		         strcpy(flm[next].filmadi,flm[sayac2+1].filmadi);				
		         strcpy(flm[sayac2+1].filmadi,temp3);
		
		         strcpy(temp3,flm[next].filmyonetmen);
		         strcpy(flm[next].filmyonetmen,flm[sayac2+1].filmyonetmen);
		         strcpy(flm[sayac2+1].filmyonetmen,temp3);
		
		         strcpy(temp3,flm[next].filmsenarist);
		         strcpy(flm[next].filmsenarist,flm[sayac2+1].filmsenarist);
		         strcpy(flm[sayac2+1].filmsenarist,temp3);
		         
		         strcpy(temp3,flm[next].filmoyuncu);
		         strcpy(flm[next].filmoyuncu,flm[sayac2+1].filmoyuncu);  
		         strcpy(flm[sayac2+1].filmoyuncu,temp3);
					
				} 
				sayac2++;
			}
	   sayac2=0;					//Bir sonraki filmleri kontrol edebilmesi için buradaki verileri birer birer arttırıyoruz...
	   j++;
	   sayac2+=j;					//Bubblesorttaki mantık gibi...
	   sayac1--;
	   next++;
		}
		fclose(fp1);
		i=0;
		printf("Dosyadaki filmler\n");
	
		
		while(strcmp(flm[i].filmadi,"")!=0){
			
			printf("%s %s %s %s %s\n",flm[i].filmadi,flm[i].filmyonetmen,flm[i].filmsenarist,flm[i].filmoyuncu,flm[i].filmyil);
			i++;
			
		}
		
		_getch();
	}
	
	if(secim==4){
	

		typedef proje film;
		film flm;
		
		char bilgi[1000];
		
		printf("Guncellemek istediginiz filmi seciniz: "); 
		scanf("%s",bilgi);
		
		FILE *fp11=fopen("Filmler.txt","r");
		FILE *fp12=fopen("Filmler1.txt","w");
		

		
		if(fp11==NULL)  printf("Aradiginiz film bulunamadi"); // Eger ki dosyada film yoksa uyarı mesajı vericek...
		
		
		while(!feof(fp11)){
			
			fscanf(fp11,"%s %s %s %s %s\n",flm.filmadi,flm.filmyonetmen,flm.filmsenarist,flm.filmoyuncu,flm.filmyil);
				if(strstr(flm.filmadi,bilgi))
				{
					printf("Lutfen guncellestireceginiz filmin yeni bilgilerini giriniz\n");
					printf("Filmin adi:"); scanf("%s",flm.filmadi);
					printf("Filmin yonetmeni:");scanf("%s",flm.filmyonetmen);
					printf("Filmin senaristi:");scanf("%s",flm.filmsenarist);
					printf("Filmin basrol oyuncusu");scanf("%s",flm.filmoyuncu);
					printf("Filmin yili:");scanf("flm.filmyil");
					
				}
				fprintf(fp12,"%s %s %s %s %s\n",flm.filmadi,flm.filmyonetmen,flm.filmsenarist,flm.filmoyuncu,flm.filmyil);
				
				printf("Guncellestirmek istediginiz film basariyla guncellestirildi\tSu anda menuye yonlendiriliyorsunuz...\n");
			
		}
	
		
		
	fclose(fp11);
	fclose(fp12);
	FILE *icdoldur;
	if(icdoldur=fopen("Filmler.txt","w")){
	FILE *icoku=fopen("Filmler1.txt","r");//Burada bir tane daha dosya açıyoruz ve ilk dosyadaki verilerin eski halini okumadan yeni haline yani açtıgımız dosyaya yazdırıyoruz...
	char okunan[100];
	while(!feof(icoku)){
	fscanf(icoku,"%s",okunan);
	fprintf(icdoldur,"%s\n",okunan);
	}
	
	
	
}


}
	
	if(secim==5){
		
		typedef proje film;
		film flm;
		
		char bilgi[1000],karar[15];
		
		printf("Silmek istediginiz filmi seciniz: "); 
		scanf("%s",bilgi);
		
		FILE *fp9=fopen("Filmler.txt","r");
		FILE *fp10=fopen("Filmler1.txt","w");
		

		
		if(fp9==NULL)  printf("Aradiginiz film bulunamadi"); // Eger ki dosyada film yoksa uyarı mesajı vericek...
		
		printf("Filmi silmek istediginize emin misiniz?silmek icin 'e' menuye donmek icin 'h' ye basınız...");
		scanf("%s",karar);
		if(strcmp(karar,"e")==0){
			
			fscanf(fp9,"%s %s %s %s %s\n",flm.filmadi,flm.filmyonetmen,flm.filmsenarist,flm.filmoyuncu,flm.filmyil);
				if(strstr(flm.filmadi,bilgi))
				{
					continue;
				}
				fprintf(fp10,"%s %s %s %s %s\n",flm.filmadi,flm.filmyonetmen,flm.filmsenarist,flm.filmoyuncu,flm.filmyil);
				
				printf("Silmek istediginiz film basariyla silindi\tSu anda menuye yonlendiriliyorsunuz...");
			
		}
		else if(strcmp(karar,"h")==0)
		{
			printf("\nh secenegini sectiginiz icin film silinemedi...");
			printf("\nAna Menuye Donmek Icin Herhangi Bir Tusa Basiniz...");
			_getch();
			system("CLS");
			return main();
		}
		
		
	fclose(fp9);
	fclose(fp10);
	FILE *icdoldur;
	if(icdoldur=fopen("Filmler.txt","w")){
	FILE *icoku=fopen("Filmler1.txt","r");
	char okunan[100];
	while(!feof(icoku)){
	fscanf(icoku,"%s",okunan);
	fprintf(icdoldur,"%s\n",okunan);
	}
	
	
	
}
}

	
	
	if(secim==6){
		
		
			printf("Hoscakalin...");
			
			return 0;
}

	
	
	}



}
