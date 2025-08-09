```cs
using System;
using System.Collections.Generic;

namespace VehicleApp
{
    // ✅ Parent Class
    class Vehicle
    {
        public string ModelNo { get; set; }
        public double Mileage { get; set; }
        public double CC { get; set; }

        public Vehicle(string modelNo, double mileage, double cc)
        {
            ModelNo = modelNo;
            Mileage = mileage;
            CC = cc;
        }

        // ✅ Virtual method for Polymorphism
        public virtual void ShowDetails()
        {
            double dualConsumption = CC * Mileage;
            Console.WriteLine($"Model No: {ModelNo}");
            Console.WriteLine($"Mileage: {Mileage} km/l");
            Console.WriteLine($"CC: {CC}");
            Console.WriteLine($"Dual Consumption: {dualConsumption}");
        }
    }

    // ✅ Child Classes
    class Car : Vehicle
    {
        public Car() : base("Car123", 15.5, 1500) { }

        public override void ShowDetails()
        {
            Console.WriteLine("🚗 Car Details:");
            base.ShowDetails();
        }
    }

    class Truck : Vehicle
    {
        public Truck() : base("Truck456", 8.0, 5000) { }

        public override void ShowDetails()
        {
            Console.WriteLine("🚚 Truck Details:");
            base.ShowDetails();
        }
    }

    class Bus : Vehicle
    {
        public Bus() : base("Bus789", 6.5, 4000) { }

        public override void ShowDetails()
        {
            Console.WriteLine("🚌 Bus Details:");
            base.ShowDetails();
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // ✅ Polymorphism using List
            List<Vehicle> vehicles = new List<Vehicle>
            {
                new Car(),
                new Truck(),
                new Bus()
            };

            // ✅ Loop through list and show details
            foreach (Vehicle v in vehicles)
            {
                v.ShowDetails();
                Console.WriteLine("----------------------------");
            }

            Console.ReadLine();
        }
    }
}

```
