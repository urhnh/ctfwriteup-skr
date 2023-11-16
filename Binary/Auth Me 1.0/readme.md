# Challenge

![Auth Me 1 0](https://github.com/urhnh/ctfwriteup/assets/149639198/cb5ac3d4-f241-4047-85bf-b5e334016ec4)

# Solution

- Open web shell, login team name
  
- cd challenges/auth_me (to change directory)
  
- ls (to list files in the current directory)

- cat auth.c (to view the source code)
  
![webshell 1](https://github.com/urhnh/ctfwriteup/assets/149639198/2f04f871-8bb1-4ad9-a0d9-578af7cfd60e)

'''c

#include <stdio.h>                                                                                                                                   
#include <stdlib.h>                                                                                                                                  
#include <string.h>                                                                                                                                  
#include <signal.h>                                                                                                                                  
                                                                                                                                                     
#define FLAGSIZE_MAX 64                                                                                                                              
                                                                                                                                                     
char flag[FLAGSIZE_MAX];                                                                                                                             
                                                                                                                                                     
void setup(){                                                                                                                                        
  FILE *f = fopen("flag.txt","r");                                                                                                                   
  fgets(flag,FLAGSIZE_MAX,f);                                                                                                                        
  gid_t gid = getegid();                                                                                                                             
  setresgid(gid, gid, gid);                                                                                                                          
}                                                                                                                                                    
                                                                                                                                                     
int main(int argc, char **argv){                                                                                                                     
  setup();                                                                                                                                           
  int authed = 0;                                                                                                                                    
  char user[16];                                                                                                                                     
  printf("Authenticate Me 1.0\n");                                                                                                                   
  printf("--------------------------------\n");                                                                                                      
  printf("Enter your username: ");                                                                                                                   
  gets(user);                                                                                                                                        
  // Haven't implement login function yet                                                                                                            
  if(authed){                                                                                                                                        
    printf("Welcome admin! Here is your flag: %s",flag);                                                                                             
  }else{                                                                                                                                             
    printf("Good Bye %s\n",user);                                                                                                                    
  }                                                                                                                                                  
  return 0;                                                                                                                                          
}                 

'''
