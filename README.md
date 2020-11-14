# 7.2-
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace DISKRETKA
{    // реализация перестановки через рекурссию
    class Program 
    {
        static void Swap<T>(ref T v1, ref T v2)
        {
            T v3 = v1;
            v1 = v2;
            v2 = v3;
        }

        static void generate(int t, int n, int [] a)
        {
            if (t == n - 1)
            {                                 //Вывод очередной перестановки
                for (int i = 0; i < n; ++i)
                    Console.Write(a[i]);
                Console.WriteLine();
            }
            else
            {
                for (int j = t; j < n; ++j)
                {                             //Запускаем процесс обмена
                    Swap(ref a[t], ref a[j]); //a[t] со всеми последующими
                    t++;
                    generate(t, n, a);
                                              
                    t--;
                    Swap(ref a[t], ref a[j]);
                }
            }
        }

        static void Main(string[] args)
        {
            int n = Convert.ToInt32(Console.ReadLine());
            int[] a = new int[n];
            for (int i = 0; i < n; i++)
                a[i] = i + 1;
            generate(0, n, a);

            Console.ReadKey();
        }
    }
}
