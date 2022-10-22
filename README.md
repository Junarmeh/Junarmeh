using System;

class Program
{
    static void Main(string[] args)
    {
        //Değerleri tanımladık

        int AX;
        int AY;
        int Ahealth;
        int Aset;
        int BX;
        int BY;
        int Bhealth;
        int Bset;
        int CX;
        int CY;
        int Chealth;
        int Cset;


        // A oyuncusunu oluşturduk. Kullanıcıdan koordinat girmesini istedik

        Console.WriteLine("Enter the location of A: ");
        Console.Write("AX: ");
        AX = Convert.ToInt16(Console.ReadLine());
        Console.Write("AY: ");
        AY = Convert.ToInt16(Console.ReadLine());


        if (AX > 10 || AX < -10 || AY > 10 || AY < -10) // girilen koordinatlar şartı sağlamazsa program kapanıyor. 
        {
            Console.WriteLine("You can't enter this value!"); 
        }
        else //program devam ediyor
        {

            Random rnd = new Random();
            Aset = rnd.Next(1, 4);
            Ahealth = rnd.Next(3, 6) * 20;

            Console.WriteLine("A : " + "(" + AX + "," + AY + ")  " + "Set " + Aset + "   Health: " + Ahealth);




            // B okçusunun özelliklerini girdik.

            //b'ye rastgele set
            Bset = rnd.Next(1, 4);
            if (Aset == 1)
            {
                Bset = rnd.Next(2, 4);
            }

            else if (Aset == 3)
            {
                Bset = rnd.Next(1, 3);
            }

            else if (Aset == 2)
            {
                int gecici = rnd.Next(0, 2);
                if (gecici == 0)
                {
                    Bset = 1;
                }

                else
                {
                    Bset = 3;
                }
            }


            //b'ye rastgele health
            Bhealth = rnd.Next(3, 6) * 20;

            if (Ahealth == 60)
            {
                Bhealth = rnd.Next(4, 6) * 20;
            }

            else if (Ahealth == 100)
            {
                Bhealth = rnd.Next(3, 5) * 20;
            }

            else if (Ahealth == 80)
            {
                int gecici = rnd.Next(0, 2);
                if (gecici == 0)
                {
                    Bhealth = 60;
                }

                else
                {
                    Bhealth = 100;
                }
            }

            //b'ye rastgele koordinatlar
            Random rndcoordinate = new Random();
            BX = rndcoordinate.Next(-10, 11);
            BY = rndcoordinate.Next(-10, 11);
            Console.WriteLine("B : " + "(" + BX + "," + BY + ") " + "Set " + Bset + "   Health: " + Bhealth);



            // C okçusunun özelliklerini girdik.



            Cset = rnd.Next(1, 4);
            if ((Aset == 1 && Bset == 2) || (Aset == 2 && Bset == 1))
            {
                Cset = 3;
            }

            else if ((Aset == 1 && Bset == 3) || (Aset == 3 && Bset == 1))
            {
                Cset = 2;
            }

            else if ((Aset == 2 && Bset == 3) || (Aset == 3 && Bset == 2))
            {
                Cset = 1;
            }



            //c'ye rastgele health

            Chealth = rnd.Next(3, 6) * 20;

            if ((Ahealth == 60 && Bhealth == 80) || (Ahealth == 80 && Bhealth == 60))
            {
                Chealth = 100;
            }

            else if ((Ahealth == 60 && Bhealth == 100) || (Ahealth == 100 && Bhealth == 60))
            {
                Chealth = 80;
            }

            else if ((Ahealth == 80 && Bhealth == 100) || (Ahealth == 100 && Bhealth == 80))
            {
                Chealth = 60;
            }


            //c'ye rastgele koordinatlar

            CX = rndcoordinate.Next(-10, 11);
            CY = rndcoordinate.Next(-10, 11);
            Console.WriteLine("C : " + "(" + CX + "," + CY + ") " + "Set " + Cset + "   Health: " + Chealth);



            //koordinat
            Console.WriteLine("   +---------------------+");
            Console.WriteLine(" 10|..........|..........|");
            Console.WriteLine("  9|..........|..........|");
            Console.WriteLine("  8|..........|..........|");
            Console.WriteLine("  7|..........|..........|");
            Console.WriteLine("  6|..........|..........|");
            Console.WriteLine("  5|..........|..........|");
            Console.WriteLine("  4|..........|..........|");
            Console.WriteLine("  3|..........|..........|");
            Console.WriteLine("  2|..........|..........|");
            Console.WriteLine("  1|..........|..........|");
            Console.WriteLine("  0|----------+---------->");
            Console.WriteLine(" -1|..........|..........|");
            Console.WriteLine(" -2|..........|..........|");
            Console.WriteLine(" -3|..........|..........|");
            Console.WriteLine(" -4|..........|..........|");
            Console.WriteLine(" -5|..........|..........|");
            Console.WriteLine(" -6|..........|..........|");
            Console.WriteLine(" -7|..........|..........|");
            Console.WriteLine(" -8|..........|..........|");
            Console.WriteLine(" -9|..........|..........|");
            Console.WriteLine("-10|..........|..........|");
            Console.WriteLine("   +---------------------+");
            Console.WriteLine("    098765432101234567890");



            Console.SetCursorPosition(AX + 14, Math.Abs(AY - 17));
            Console.WriteLine("A");


            Console.SetCursorPosition(BX + 14, Math.Abs(BY - 17));
            Console.WriteLine("B");

            Console.SetCursorPosition(CX + 14, Math.Abs(CY - 17));
            Console.WriteLine("C");



            Console.SetCursorPosition(5, Math.Abs(-32));
            int aX = AX - BX;
            int aY = AY - BY;
            double distance1 = Math.Sqrt(aX * aX + aY * aY);



            int bX = BX - CX;
            int bY = BY - CY;
            double distance2 = Math.Sqrt(bX * bX + bY * bY);



            int cX = AX - CX;
            int cY = AY - CY;
            double distance3 = Math.Sqrt(cX * cX + cY * cY);
            /*   //1.YOL
            double min = distance1;
            if (distance2 < min)
            {
                min = distance2;
            }
            if (distance3 < min)
            {
                min = distance3;
            }

            if (min == distance1)
            {
                if (distance1 > 15)
                {
                    Console.WriteLine("Too Distant, No Attack");
                }
                else
                {
                    Console.WriteLine("ROUND 1 : A-B");
                }
            }

            else if (min == distance2)
            {
                if (distance2 > 15)
                {
                    Console.WriteLine("Too Distant, No Attack");
                }
                else 
                {
                    Console.WriteLine("ROUND 1 : B-C");
                }
            }
            else
            {
                if (distance3 > 15)
                {
                    Console.WriteLine("Too Distant, No Attack");
                }
                else
                {
                    Console.WriteLine("ROUND 1 : A-C");
                    
                }
            } 


            Console.ReadKey(); */











            // 2.YOL
            
            if (distance1 < distance2 && distance1 < distance3)
            {
                Console.WriteLine("ROUND 1 : A-B");
            }
            if (distance1 > 15)
            {
                Console.WriteLine("Too Distant, No Attack");
            }
            if (distance2 < distance1 && distance2 < distance3)
            {
                Console.WriteLine("ROUND 1 : B-C");
                if (distance2 > 15)
                {
                    Console.WriteLine("Too Distant, No Attack");
                }
            }

            if (distance3 < distance2 && distance3 < distance1)
            {
                Console.WriteLine("ROUND 1 : A-C");
                if (distance3 > 15)
                {
                    Console.WriteLine("Too Distant, No Attack");
                }
                Console.ReadKey();
            } 
            Console.ReadKey();



























        }




    }
}







