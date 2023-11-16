# Challenge

![challenge](https://github.com/urhnh/ctfwriteup/assets/149639198/59bc45d9-2b52-4b6f-a8b0-29d556376962)

# Solution

- Solve it using maths!

```
#include <stdio.h>

int main () {
	char password[16];
	printf("Enter password: ");
	scanf("%s",password);
	int pass = atoi(password);
	if ((pass*2)-666 == 2008)
	{
		printf("Welcome admin!\nFlag: SKR{%s}",password);
	}else{
		printf("Login failed!");
	}
}
```

