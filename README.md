<div align="center">

## Search a string from textfile


</div>

### Description

Searches if a textfile contains a string that you specify. If matching string is found, the line# and the line, where your searchstring was found, will be printed to the screen. Searchstring is case sensitive.
 
### More Info
 
filename as argv[1], and string to search as argv[2].

Line# and the line where the string was found.


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Markku Kauppinen](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/markku-kauppinen.md)
**Level**          |Intermediate
**User Rating**    |3.8 (19 globes from 5 users)
**Compatibility**  |C
**Category**       |[Strings](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/strings__3-26.md)
**World**          |[C / C\+\+](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/c-c.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/markku-kauppinen-search-a-string-from-textfile__3-6070/archive/master.zip)





### Source Code

```
/*************************************************************************
 License : You're free to use this piece of code in your projects.
 But if you use it, drop me an email about it, or greet me
 in your project notes.
*************************************************************************/
#include <stdio.h>
#include <string.h>
char searchstring(char*, char*);
#define linelength 250
int main(int argc, char* argv[])
{
 if( argc != 3 ) {
 printf("Usage: search.exe <filename> \"<searchstring>\"\n");
 return 1;
 }
 searchstring(argv[1], argv[2]);
 return 0;
}
char searchstring(char* filename, char* string)
{
 FILE* file;
 char buffer[linelength];
 int line=0;
 unsigned int x, y, u;
 if( (file = fopen(filename, "rb")) == NULL ) {
 printf("File read error!\n");
 return 1;
 }
 while(1) {
 y = 0;
 u = 0;
 fgets(buffer, linelength, file);
 line++;
 if( feof(file) ) {
 break;
 }
 for(x = 0; x < strlen(buffer); x++) {
 if( buffer[y] == string[u] ) {
  y++;
  u++;
  if( u == strlen(string) ) {
  printf("Line %d: %s", line, buffer);
  }
 }
 if( buffer[y] != string[u] ) {
  u = 0;
  y++;
 }
 }
 }
 fclose(file);
 return 0;
}
```

