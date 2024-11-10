using System;
using System.Collections.Generic;
using System.Linq;

class Program
{
    static void Main()
    {
        while (true)
        {
            Console.WriteLine("\n--- Main Menu ---");
            Console.WriteLine("1. Sum Calculation with Triple Condition");
            Console.WriteLine("2. Voting Eligibility Check");
            Console.WriteLine("3. Coordinate Quadrant Check");
            Console.WriteLine("4. Triangle Type Detection");
            Console.WriteLine("5. Electricity Bill Calculation");
            Console.WriteLine("6. Bank System (Deposit, Withdraw, Check Balance)");
            Console.WriteLine("7. Student Grades Analysis");
            Console.WriteLine("8. Exit");
            Console.Write("Select an option: ");
            int choice = int.Parse(Console.ReadLine());

            if (choice == 8) break;

            switch (choice)
            {
                case 1:
                    SumCalculation();
                    break;
                case 2:
                    VotingEligibility();
                    break;
                case 3:
                    CoordinateQuadrant();
                    break;
                case 4:
                    TriangleType();
                    break;
                case 5:
                    ElectricityBill();
                    break;
                case 6:
                    BankSystem();
                    break;
                case 7:
                    StudentGradesAnalysis();
                    break;
                default:
                    Console.WriteLine("Invalid choice. Please try again.");
                    break;
            }
        }
    }

    // Exercise 1 - Part 1: Sum Calculation with Triple Condition
    static void SumCalculation()
    {
        Console.WriteLine("Enter first number:");
        int num1 = int.Parse(Console.ReadLine());
        Console.WriteLine("Enter second number:");
        int num2 = int.Parse(Console.ReadLine());
        int sum = num1 + num2;
        Console.WriteLine("Result: " + (num1 == num2 ? sum * 3 : sum));
    }

    // Exercise 1 - Part 2: Voting Eligibility Check
    static void VotingEligibility()
    {
        Console.WriteLine("Enter age:");
        int age = int.Parse(Console.ReadLine());
        Console.WriteLine(age > 18 ? "Eligible to vote." : "Not eligible to vote.");
    }

    // Exercise 1 - Part 3: Coordinate Quadrant Check
    static void CoordinateQuadrant()
    {
        Console.WriteLine("Enter X coordinate:");
        int x = int.Parse(Console.ReadLine());
        Console.WriteLine("Enter Y coordinate:");
        int y = int.Parse(Console.ReadLine());

        if (x > 0 && y > 0)
            Console.WriteLine("First Quadrant");
        else if (x < 0 && y > 0)
            Console.WriteLine("Second Quadrant");
        else if (x < 0 && y < 0)
            Console.WriteLine("Third Quadrant");
        else if (x > 0 && y < 0)
            Console.WriteLine("Fourth Quadrant");
        else
            Console.WriteLine("Origin");
    }

    // Exercise 1 - Part 4: Triangle Type Detection
    static void TriangleType()
    {
        Console.WriteLine("Enter side1:");
        int side1 = int.Parse(Console.ReadLine());
        Console.WriteLine("Enter side2:");
        int side2 = int.Parse(Console.ReadLine());
        Console.WriteLine("Enter side3:");
        int side3 = int.Parse(Console.ReadLine());

        if (side1 == side2 && side2 == side3)
            Console.WriteLine("Equilateral Triangle");
        else if (side1 == side2 || side2 == side3 || side1 == side3)
            Console.WriteLine("Isosceles Triangle");
        else
            Console.WriteLine("Scalene Triangle");
    }

    // Exercise 1 - Part 5: Electricity Bill Calculation
    static void ElectricityBill()
    {
        Console.WriteLine("Enter units consumed:");
        int units = int.Parse(Console.ReadLine());
        double charge;

        if (units < 300)
            charge = units * 1.5;
        else if (units < 450)
            charge = units * 2;
        else
            charge = units * 2.5;

        if (units > 600)
            charge *= 1.1;

        Console.WriteLine("Total Bill: " + charge);
    }

    // Exercise 2: Bank System
    static double balance = 0;

    static void BankSystem()
    {
        while (true)
        {
            Console.WriteLine("\n--- Bank Menu ---");
            Console.WriteLine("1. Deposit");
            Console.WriteLine("2. Withdraw");
            Console.WriteLine("3. Check Balance");
            Console.WriteLine("4. Back to Main Menu");
            Console.Write("Choose an option: ");
            int option = int.Parse(Console.ReadLine());

            if (option == 4) break;

            switch (option)
            {
                case 1:
                    Console.Write("Enter deposit amount: ");
                    double depositAmount = double.Parse(Console.ReadLine());
                    Deposit(depositAmount);
                    break;
                case 2:
                    Console.Write("Enter withdraw amount: ");
                    double withdrawAmount = double.Parse(Console.ReadLine());
                    Withdraw(withdrawAmount);
                    break;
                case 3:
                    CheckBalance();
                    break;
                default:
                    Console.WriteLine("Invalid option.");
                    break;
            }
        }
    }

    static void Deposit(double amount)
    {
        if (amount > 0)
        {
            balance += amount;
            Console.WriteLine("Deposited: " + amount);
        }
        else
        {
            Console.WriteLine("Invalid amount.");
        }
    }

    static void Withdraw(double amount)
    {
        if (amount > 0 && amount <= balance)
        {
            balance -= amount;
            Console.WriteLine("Withdrawn: " + amount);
        }
        else
        {
            Console.WriteLine("Invalid amount or insufficient balance.");
        }
    }

    static void CheckBalance()
    {
        Console.WriteLine("Current Balance: " + balance);
    }

    // Exercise 3: Student Grades Analysis
    static void StudentGradesAnalysis()
    {
        Console.Write("Enter number of students: ");
        int numberOfStudents = int.Parse(Console.ReadLine());
        List<int> grades = new List<int>();

        for (int i = 0; i < numberOfStudents; i++)
        {
            Console.Write($"Enter grade for student {i + 1}: ");
            grades.Add(int.Parse(Console.ReadLine()));
        }

        int minGrade = grades.Min();
        int maxGrade = grades.Max();
        double avgGrade = grades.Average();
        int aboveAverage = grades.Count(g => g > avgGrade);
        int belowAverage = grades.Count(g => g < avgGrade);

        Console.WriteLine("Minimum Grade: " + minGrade);
        Console.WriteLine("Maximum Grade: " + maxGrade);
        Console.WriteLine("Average Grade: " + avgGrade);
        Console.WriteLine("Students above average: " + aboveAverage);
        Console.WriteLine("Students below average: " + belowAverage);
    }
    
}
