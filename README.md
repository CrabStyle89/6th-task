using System;
using System.Drawing;
class GEneratingImage
{
    public static void Main(string  [] args)

    {

        int size = int.Parse(args[0]);
        int nCols = int.Parse(args[1]);
        int nRows = int.Parse(args[2]);
         
        bool isBlack = false;
        Bitmap bmp = new Bitmap(size*nCols,size*nRows);
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
        void DrawBlueSquare(Bitmap bitmap, int i, int j, int s)
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
