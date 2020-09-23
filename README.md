<div align="center">

## Text encrypter


</div>

### Description

*UPDATED* Now uses a more recursive and less pattern oriented algorithm.

Basically encrypts a text type file using a simple recursive character shift techinque. Pretty basic, but powerful.
 
### More Info
 
Takes an input file name, an output file name, and a key

creates(or over-writes) an output file

This program will automatically overwrite any file that you specify as the output file


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Evan Hartman](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/evan-hartman.md)
**Level**          |Beginner
**User Rating**    |5.0 (10 globes from 2 users)
**Compatibility**  |C
**Category**       |[Security](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/security__3-14.md)
**World**          |[C / C\+\+](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/c-c.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/evan-hartman-text-encrypter__3-581/archive/master.zip)

### API Declarations

```
conio.h
stdio.h
stdlib.h
```


### Source Code

```
#include	<stdio.h>
#include	<conio.h>
#include	<stdlib.h>
#include	<math.h>
FILE	*stream;
FILE	*streamout;
//	The key can be up to 100 characters,
//	will accept and use spaces, and is
//	case sensitive. The only way to decypher
//	the file is to know the key. Kinda neat,
//	because even if you know the algorithm,
//	it doesn't do you any good.
int main(int argc, char *argv[]){
	char			y;
	int				x;
	int				z;
	int				i;
	unsigned char	input[100];
	unsigned char	output[100];
	unsigned char	key[100];
	printf("Enter Input Filename -> ");
	scanf("%s",input);
	printf("Enter Output Filename -> ");
	scanf("%s",output);
	getchar();
	printf("Enter Key -> ");
	scanf("%[^\n]",key);
	stream=fopen(input,"r");
	streamout=fopen(output,"w");
	z=1;
	do{
		y=fgetc(stream);
		if(y!=EOF){
			x=(int)y;
			for(i=0;key[i];i++)
				x=x^key[i];
			x^=z;
			z^=2^z;
			fprintf(streamout,"%c",x);
		}
	}while(y!=EOF);
	fclose(stream);
	fclose(streamout);
	printf("press any key to continue");
	while(!kbhit());  //wait to exit
	return 0;
}
```

