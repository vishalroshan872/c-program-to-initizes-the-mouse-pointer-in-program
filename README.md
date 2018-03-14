#include<graphics.h>
#include<conio.h>
#include<dos.h>

int initmouse();
void showmouseptr();

union REGS i, o;

main()
{
   int status, gd = DETECT, gm;

   initgraph(&gd,&gm,"C:\\TC\\BGI");

   status = initmouse();

   if ( status == 0 )
      printf("Mouse support not available.\n");
   else
      showmouseptr();

   getch();
   return 0;
}

int initmouse()
{
   i.x.ax = 0;
   int86(0X33,&i,&o);
   return ( o.x.ax );
}

void showmouseptr()
{
   i.x.ax = 1;
   int86(0X33,&i,&o);
}# c-program-to-initizes-the-mouse-pointer-in-program
this c source code is used to initiazes the mouse pionter in any program apps
