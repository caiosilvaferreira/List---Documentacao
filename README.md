# List

![Untitled](List%205f3d9b6e1a8647a49ca2876a92f9bee6/Untitled.png)

codigo abaixo explicando como fazer uma lista e outras funcoes

```csharp
using System.Globalization;
using System.Runtime.CompilerServices;

namespace Course {
    class Produto1 {
        static void Main(string[] args) {

            List<string> list = new List<string>();

            list.Add("maria");
            list.Add("caio"); // adiciona uma string no nodo
            list.Add("breno");
            list.Add("isabela");
            list.Add("mario");
            list.Insert(1, "novato"); // inseri no nodo que a pessoa escolher

            foreach(string obj in list) {
                Console.WriteLine(obj);
            }

            Console.WriteLine("list count = " + list.Count); // conta a totalidade da lista

            string s1 = list.Find(x => x[0] =='b');  // primeiro nome que começa com a letra b
            Console.WriteLine("first name this b : "+ s1);

            string s2 = list.FindLast(x => x[0] == 'm');
            Console.WriteLine("last name this m = " + s2);   // ultimo nome que começa com a letra m

            int pos1 = list.FindIndex(x => x[0] == 'm');
            Console.WriteLine("posicao do nome que começa com letra m = "+ pos1);

            int pos2 = list.FindLastIndex(x => x[0] == 'm');
            Console.WriteLine("posicao do nome que começa com letra m = "+ pos2);

            List<string> list2 = list.FindAll(x => x.Length == 5);

            foreach (string obj in list2) {
                Console.WriteLine("nomes que começam com 5 caracteres = " +obj);
                Console.WriteLine("-----------------------------------------------");
            }

            list.Remove("caio");

            foreach (string obj in list) {
                Console.WriteLine("removendo o nome caio =  " +obj);
            }

            list.RemoveAll(x => x[0] =='m');

            foreach (string obj in list) {
                Console.WriteLine("removendo todos os nomes com a letra inicial m =  " +obj);
            }

            list.RemoveAt(1); // remove de acordo com a posição
            foreach (string obj in list) {
                Console.WriteLine("removendo o primeiro nome =  " +obj);
            }

            list.RemoveRange(1, 5); // começa removendo na posição 1 ate o 5
        }
    }
}
```

não resolvir o exercicio de lista, mas vou deixar o codigo do nelio, caso precise

```csharp
using System;
using System.Globalization;
using System.Collections.Generic;

namespace Course {
    class Program {
        static void Main(string[] args) {

            Console.Write("How many employees will be registered? ");
            int n = int.Parse(Console.ReadLine());

            List<Employee> list = new List<Employee>();

            for (int i = 1; i <= n; i++) {
                Console.WriteLine("Employee #" + i + ":");
                Console.Write("Id: ");
                int id = int.Parse(Console.ReadLine());
                Console.Write("Name: ");
                string name = Console.ReadLine();
                Console.Write("Salary: ");
                double salary = double.Parse(Console.ReadLine(), CultureInfo.InvariantCulture);
                list.Add(new Employee(id, name, salary));
                Console.WriteLine();
            }

            Console.Write("Enter the employee id that will have salary increase : ");
            int searchId = int.Parse(Console.ReadLine());

            Employee emp = list.Find(x => x.Id == searchId);
            if (emp != null) {
                Console.Write("Enter the percentage: ");
                double percentage = double.Parse(Console.ReadLine(), CultureInfo.InvariantCulture);
                emp.IncreaseSalary(percentage);
            } else {
                Console.WriteLine("This id does not exist!");
            }

            Console.WriteLine();
            Console.WriteLine("Updated list of employees:");
            foreach (Employee obj in list) {
                Console.WriteLine(obj);
            }
        }
    }
}
```

```csharp
using System.Globalization;

namespace Course {
    class Employee {

        public int Id { get; set; }
        public string Name { get; set; }
        public double Salary { get; private set; }

        public Employee(int id, string name, double salary) {
            Id = id;
            Name = name;
            Salary = salary;
        }

        public void IncreaseSalary(double percentage) {
            Salary += Salary * percentage / 100.0;
        }

        public override string ToString() {
            return Id
                + ", "
                + Name
                + ", "
                + Salary.ToString("F2", CultureInfo.InvariantCulture);
        }
    }
}
```
