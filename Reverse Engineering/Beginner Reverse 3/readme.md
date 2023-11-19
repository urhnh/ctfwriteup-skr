# Challenge

![challenge](https://github.com/urhnh/ctfwriteup/assets/149639198/8ab70b55-2251-4123-afb6-93529e123167)

# Solution

```
#include <stdio.h>
#include <string.h>

int checkPassword(char* pass){
	if(strlen(pass) != 14){
		return 0;
	}
	if(strncmp(pass+2,"cur3", 4) != 0){
		return 0;
	}
	if(strncmp(pass,"S3", 2) != 0){
		return 0;
	}
	if(strncmp(pass+10,"w0rd", 4) != 0){
		return 0;
	}
	if(strncmp(pass+6,"Pa$$", 4) != 0){
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

- Quick refresh of coding

  in order for checkPassword to return 1

  - should be 14 characters
 
  - skip first 2 character, should equal to cur3
 
  - skip first 0 character, should equal to S3
 
  - skip first 10 character, should equal to w0rd
 
  - skip first 6 character, should equal to Pa$$
 
- Will get pass = S3cur3Pa$$w0rd
