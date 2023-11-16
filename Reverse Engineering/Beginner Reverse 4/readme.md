# Challenge

![challenge](https://github.com/urhnh/ctfwriteup/assets/149639198/f1f8cbdc-66c6-4ec0-857a-8aad5f12c5dd)

Hint: Keep track of the increment and decrement of i and j

# Solution

- Quick refresh of coding

  in order for checkPassword to return 1

  - should be 15 characters
 
  - pass[i] != part1[j] (int i = 0, j = 0; i < length; i+=2,j++)
 
  - pass[i] != part1[j] (int i = length-2, j = 0; i > 0; i-=2,j++)

- Will get pass = Sup3rS3cureP455

```
#include <stdio.h>
#include <string.h>

int checkPassword(char* pass){
	size_t length = strlen(pass);
	if(length != 15){
		return 0;
	}
	char* part1 = "Spr3ue45";
	for (int i = 0, j = 0; i < length; i+=2,j++){
		if(pass[i] != part1[j]){
			return 0;
		}
	}

	char* part2 = "5PrcS3u";
	for (int i = length-2, j = 0; i > 0; i-=2,j++){
		if(pass[i] != part2[j]){
			return 0;
		}
	}
	return 1;
}


int main () {
	char password[20];
	printf("Enter password: ");
	scanf("%19s",password);
	if (checkPassword(password))
	{
		printf("Welcome admin!\nFlag: SKR{%s}",password);
	}else{
		printf("Login failed!");
	}
}
```
