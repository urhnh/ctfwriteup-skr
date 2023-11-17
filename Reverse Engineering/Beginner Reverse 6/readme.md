# Challenge

![challenge](https://github.com/urhnh/ctfwriteup/assets/149639198/8a2fa47a-3b7c-4d24-b0ee-2b196f5e7c9d)

# Solution

in order for checkPassword to return 1

- should be 17 characters (length != 17)

- First letter is 'R' (pass[0] == 'R')

- Second letter and forth are '3' (pass[1] - pass[0] == -31 || pass[1] == pass[3])

- Fifth letter is 'r', third letter is 'v' (pass[4] == tolower(pass[0]) || pass[2] - pass[4] == 4)

- Sixth letter is '5', seventh letter is 1 (pass[5] == '5' || pass[5] - pass[6] == 4)

- Eight letter is 'n', ninth letter is 'G' (pass[7] == pass[0] + 28 || pass[2] - pass[8] == 47)

- Tenth letter is '_', thirteenth letter is '_', forteenth onwards 'Fun!', eleventh onwards '1s' (pass[9] == '_' || pass[12] == pass[9] || strncmp(pass+13,"Fun!",4) == 0 || strncmp(pass+10,"1s",2) == 0)

Will get pass = R3v3r51nG_1s_Fun!

```
#include <stdio.h>
#include <string.h>
#include <ctype.h>

int checkPassword(char* pass){
	size_t length = strlen(pass);
	if(length != 17){
		return 0;
	}
	if(pass[0] != 'R'){
		return 0;
	}
	if(pass[1] - pass[0] != -31 || pass[1] != pass[3]){
		return 0;
	}
	if(pass[4] != tolower(pass[0]) || pass[2] - pass[4] != 4){
		return 0;
	}
	if(pass[5] != '5' || pass[5] - pass[6] != 4){
		return 0;
	}
	if(pass[7] != pass[0] + 28 || pass[2] - pass[8] != 47){
		return 0;
	}
	if(pass[9] != '_' || pass[12] != pass[9] || strncmp(pass+13,"Fun!",4) != 0 || strncmp(pass+10,"1s",2) != 0){
		return 0;
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
