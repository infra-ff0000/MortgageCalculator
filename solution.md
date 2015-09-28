using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;


namespace MortgageCalculator
{

    class Program
    {

        public class GetMortgage
        { 

            static void Main(string[] args)
            {

                while (true)
                {
                    try
                    {

                        Console.WriteLine("Welcome. Please enter the price of the home:");

                        string input = Console.ReadLine();
  
                        decimal priceOfHome = decimal.Parse(input);

                        if (decimal.Parse(input) <= 0)
                        {
                            Console.Clear();
                            Console.WriteLine("Error: number is less than zero/invalid.");

                        }
                        else
                        {

                            Console.WriteLine("Please enter loan term in years: ");
                            string input2 = Console.ReadLine();
                            decimal yearLoanTerm = decimal.Parse(input2);

                            if (decimal.Parse(input2) <= 0)
                            {
                                Console.Clear();
                                Console.WriteLine("Error: number is less than zero/invalid.");

                            }
                            else
                            {

                                Console.WriteLine("Please enter the interest (%): ");
                                string input3 = Console.ReadLine();
                                decimal interestRate = decimal.Parse(input3);

                                if (decimal.Parse(input3) <= 0)
                                {
                                    Console.Clear();
                                    Console.WriteLine("Error: number is less than zero/invalid.");

                                }
                                else
                                {
                                    Console.WriteLine("Please enter the down payment ($): ");
                                    string input4 = Console.ReadLine();
                                    decimal downPayment = decimal.Parse(input4);

                                    if (decimal.Parse(input4) <= 0)
                                    {
                                        Console.Clear();
                                        Console.WriteLine("Error: number is less than zero/invalid.");

                                    }
                                    else
                                    {
                                    // decimal mortgage = monthlyPaymentCalc(loanTerm, yearMonths);


                                    decimal monthlyInterestRate = (interestRate * 001) / 12;
                                    decimal onePlusI = 1 + monthlyInterestRate;
                                    decimal numberOfPayments = yearLoanTerm * 12;
                                    decimal onePlusIPower = (decimal)Math.Pow((double)onePlusI, (double)numberOfPayments);
                                    //decimal yearLoanTerm = loanTerm / 12;

                                    decimal principal = priceOfHome - downPayment;
                                    decimal loanEstimate = principal / numberOfPayments;
                                    decimal payment = (principal * monthlyInterestRate) / (onePlusIPower - 1);





                                    Console.WriteLine("Your mortgage is: " + principal * ((monthlyInterestRate * onePlusIPower) / (onePlusIPower - 1)));
                                    Console.WriteLine("The number of monthly payments is: " + numberOfPayments);
                                    Console.WriteLine("The monthly payments is: " + payment);
                                    Console.WriteLine("The interest earned is: " + loanEstimate);
                                    Console.ReadLine();
                                   // Console.WriteLine("Your number of payments is:" + mortgage);
                                    Console.ReadLine();
                                    }
                                }
                            }
                        }
                    }

                    catch (FormatException e)
                    {
                        Console.Clear();
                        Console.WriteLine("Error, format of input is incorrect. Hit any key to continue.", e);
                        Console.ReadLine();
                    }
                }
            }
        }
    }
}

