using System;
using System.Drawing;
class GEneratingImage
{
    public static void Main(string  [] args)

    {

        int size = int.Parse(args[0]);                  // command line arguments
        int nCols = int.Parse(args[1]);
        int nRows = int.Parse(args[2]);
         
        bool isBlack = false;                           // my trigger to turn the color
        Bitmap bmp = new Bitmap(size*nCols,size*nRows); //creating canvas. size depends from command line
        for (int i = 0; i < bmp.Width; i+=size)
        {
            for (int j = 0; j < bmp.Height; j += size)
            {
                if (isBlack)            
                {
                    DrawBlueSquare(bmp, i, j, size);
                    isBlack = false;
                }
                else
                    isBlack = true;
            }
            isBlack = !isBlack;


        }
        void DrawBlueSquare(Bitmap bitmap, int i, int j, int s)// function for drawing 
        {
            for (int k = i; k < i + size && k < bitmap.Width; k++)
            {
                for (int l = j; l < j + size && l < bitmap.Height; l++)
                {
                    bitmap.SetPixel(k, l, Color.FromArgb(255, 0, 0, 255));
                }
            }
        }
       
        bmp.Save("Charli.bmp");

        
    }
}
