using System;

class Program
{
    static void Main()
    {
        Console.WriteLine("Simple Calculator");
        while (true)
        {
            Console.Write("Enter first number: ");
            if (!double.TryParse(Console.ReadLine(), out double num1))
            {
                Console.WriteLine("Invalid input.");
                continue;
            }

            Console.Write("Enter operator (+, -, *, /): ");
            string op = Console.ReadLine();

            Console.Write("Enter second number: ");
            if (!double.TryParse(Console.ReadLine(), out double num2))
            {
                Console.WriteLine("Invalid input.");
                continue;
            }

            double result;
            switch (op)
            {
                case "+":
                    result = num1 + num2;
                    break;
                case "-":
                    result = num1 - num2;
                    break;
                case "*":
                    result = num1 * num2;
                    break;
                case "/":
                    if (num2 == 0)
                    {
                        Console.WriteLine("Cannot divide by zero.");
                        continue;
                    }
                    result = num1 / num2;
                    break;
                default:
                    Console.WriteLine("Unknown operator.");
                    continue;
            }

            Console.WriteLine($"Result: {result}");

            Console.Write("Do you want to perform another calculation? (y/n): ");
            string answer = Console.ReadLine();
            if (answer?.Trim().ToLower() != "y")
                break;
        }
    }
}
