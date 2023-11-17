# Challenge

![challenge](https://github.com/urhnh/ctfwriteup/assets/149639198/fbbb5cdf-9e93-4f21-ade5-6fe035503654)

Hint: What is ASCII?

# Solution

in order for checkPassword to return 1

- should be 15 characters

- pass[i] == correct_pass[i]-1 (int i = 0; i < length; i++)

- refer to ascii table below, every char in 'BTDJJ`Qmvt`1o4' is replaced by char before it

![ascii table](https://github.com/urhnh/ctfwriteup/assets/149639198/4d49cc26-85b3-4560-ba87-49d0416f747e)

Will get pass = ASCII_Plus_0n3

```
#include <stdio.h>
#include <string.h>

int checkPassword(char* pass){
	size_t length = strlen(pass);
	if(length != 14){
		return 0;
	}
	char* correct_pass = "BTDJJ`Qmvt`1o4";
	for (int i = 0; i < length; i++){
		if(pass[i] != correct_pass[i]-1){
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
