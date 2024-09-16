

### **String** 

#### Declaration


```c
char * name = "John Smith"; //read only
char name[] = "John Smith"; //for manipulation
char name[11]="John Smith"; //same energy
```

#### Formatting

```c
char * name = "John Smith";
int age = 27;

/* prints out 'John Smith is 27 years old.' */
printf("%s is %d years old.\n", name, age);
```

#### **Length**

```c
char * name = "Nikhil";
printf("%d\n",strlen(name));
```

#### **Comparaison**

The function `strncmp` compares between two strings, returning the number 0 if they are equal, or a different number if they are different. The arguments are the two strings to be compared, and the maximum comparison length. There is also an unsafe version of this function called `strcmp`, but it is not recommended to use it. For example:

```c
char * name = "John";

if (strncmp(name, "John", 4) == 0) {
    printf("Hello, John!\n");
} else {
    printf("You are not John. Go away.\n");
}
```


####  **String Concatenation**

The function 'strncat' appends first n characters of src string to the destination string where n is min(n,length(src)); The arguments passed are destination string, source string, and n - maximum number of characters to be appended. For Example:

```c
#include <stdio.h>
#include <string.h>
int main() {
char dest[20]="Hello";
char src[20]="World";
strncat(dest,src,3);
printf("%s\n",dest);
strncat(dest,src,20);
printf("%s\n",dest);
  return 0;
}
```

### **Loop directives**

There are two important loop directives that are used in conjunction with all loop types in C - the `break` and `continue` directives.

The `break` directive halts a loop after ten loops, even though the while loop never finishes:

```c
int n = 0;
while (1) {
    n++;
    if (n == 10) {
        break;
    }
}
```

In the following code, the `continue` directive causes the `printf` command to be skipped, so that only even numbers are printed out:

```c
int n = 0;
while (n < 10) {
    n++;

    /* check that n is odd */
    if (n % 2 == 1) {
        /* go back to the start of the while block */
        continue;
    }

    /* we reach this code only if n is even */
    printf("The number %d is even.\n", n);
}
```

### **Static**

`static` is a keyword in the C programming language. It can be used with variables and functions.



By default, variables are local to the scope in which they are defined. Variables can be declared as static to increase their scope up to file containing them. As a result, thes

```c
#include<stdio.h>
#include<stdlib.h>


typedef struct {
    char * name;
    int age;
} person;




int runner()
{
    static int count = 0;
    count++;
    return count;
}

int main()
{
    printf("%d ", runner()); //1
    printf("%d ", runner()); //2  
    person * myperson = (person *) malloc(sizeof(person));
	
	myperson->name = "John";
	myperson->age = 27;
	printf("%s",&myperson->name);
	free(myperson);
	printf("%s",&myperson->name);
    return 0;
}


```

By default, functions are global in C. If we declare a function with `static`, the scope of that function is reduced to the file containing it.

The syntax looks like this:

```c
static void fun(void) {
   printf("I am a static function.");
}
```

 Static vs Global?

While static variables have scope over the file containing them making them accessible only inside a given file, global variables can be accessed outside the file too

### Dynamic Allocation

```c
#include<stdio.h>
#include<stdlib.h>


typedef struct {
    char * name;
    int age;
} person;






int main()
{
    
    person * myperson = (person *) malloc(sizeof(person));
	
	myperson->name = "John";
	myperson->age = 27;
	printf("%s",&myperson->name);
	free(myperson);
	printf("%s",&myperson->name);
    return 0;
}

```