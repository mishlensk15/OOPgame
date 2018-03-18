# OOPgame
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace OOPgame
{
 class Game
    {
        public int min, max;
        private int zagad;

        public Game(int max, int min)
        {
            this.max = max;
            this.min = min;
        }

        public void rand()
        {
            Random rnd = new Random();
            zagad= rnd.Next(min, max);
        }

        public string Otvet(int chislo)
        {
            if (chislo > max || chislo < min)
            {
                return "Ваше число за межами дiапазону.";
            }
            else
            {
                if (chislo > zagad)
                {
                    max = chislo;
                    return "Ви не вгадали( Спробуйте ще раз.";
                }
                else if(chislo==zagad)
                {

                    return "Перемога!";
                }
                else
                {
                    min = chislo;
                    return "Ви не вгадали( Спробуйте ще раз";
                }

            }
        }


    }
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Вiтаємо у грi Вгадай число!");
            Console.WriteLine("Правила: компьютер загадує число в дiапазонi вiд 1 до 100, а Ви його вгадуєте.");
            Console.WriteLine("Будьте уважнi! Кожна ваша вiдповiдь змiнює дiапазон чисел.");
            Game igra = new Game(max: 100, min: 1);
            igra.rand();
            int chislo;
            int k=0;
            do
            {
                Console.WriteLine("Введiть число");
                chislo = Convert.ToInt16(Console.ReadLine());
                k++;
                Console.WriteLine(igra.Otvet(chislo));
            } while (igra.Otvet(chislo) != "Перемога!");
            Console.WriteLine("Ви перемогли за " + k + " ходiв.");
            Console.ReadLine();
        }
    }
}
