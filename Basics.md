# Uswer polimorphisom
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
## use Abstraction 
```cs
using System;
using System.Collections.Generic;

namespace VehicleApp
{
    abstract class Vehicle
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

        public abstract void ShowDetails();

        public double CalculateDualConsumption()
        {
            return CC * Mileage;
        }
    }

    class Car : Vehicle
    {
        public Car(string modelNo, double mileage, double cc)
            : base(modelNo, mileage, cc) { }

        public override void ShowDetails()
        {
            Console.WriteLine("🚗 Car Details:");
            Console.WriteLine($"Model No: {ModelNo}");
            Console.WriteLine($"Mileage: {Mileage} km/l");
            Console.WriteLine($"CC: {CC}");
            Console.WriteLine($"Dual Consumption: {CalculateDualConsumption()}");
        }
    }

    class Truck : Vehicle
    {
        public Truck(string modelNo, double mileage, double cc)
            : base(modelNo, mileage, cc) { }

        public override void ShowDetails()
        {
            Console.WriteLine("🚚 Truck Details:");
            Console.WriteLine($"Model No: {ModelNo}");
            Console.WriteLine($"Mileage: {Mileage} km/l");
            Console.WriteLine($"CC: {CC}");
            Console.WriteLine($"Dual Consumption: {CalculateDualConsumption()}");
        }
    }

    class Bus : Vehicle
    {
        public Bus(string modelNo, double mileage, double cc)
            : base(modelNo, mileage, cc) { }

        public override void ShowDetails()
        {
            Console.WriteLine("🚌 Bus Details:");
            Console.WriteLine($"Model No: {ModelNo}");
            Console.WriteLine($"Mileage: {Mileage} km/l");
            Console.WriteLine($"CC: {CC}");
            Console.WriteLine($"Dual Consumption: {CalculateDualConsumption()}");
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            List<Vehicle> vehicles = new List<Vehicle>();

            for (int i = 0; i < 3; i++)
            {
                Console.WriteLine("Enter vehicle type (car/truck/bus): ");
                string type = Console.ReadLine().Trim().ToLower();

                Console.Write("Enter Model No: ");
                string modelNo = Console.ReadLine();

                Console.Write("Enter Mileage (km/l): ");
                double mileage = Convert.ToDouble(Console.ReadLine());

                Console.Write("Enter CC: ");
                double cc = Convert.ToDouble(Console.ReadLine());

                Vehicle vehicle = null;

                switch (type)
                {
                    case "car":
                        vehicle = new Car(modelNo, mileage, cc);
                        break;
                    case "truck":
                        vehicle = new Truck(modelNo, mileage, cc);
                        break;
                    case "bus":
                        vehicle = new Bus(modelNo, mileage, cc);
                        break;
                    default:
                        Console.WriteLine("Invalid vehicle type! Try again.");
                        i--; // decrement to repeat input for this iteration
                        continue;
                }

                vehicles.Add(vehicle);
                Console.WriteLine();
            }

            Console.WriteLine("Vehicle Details:\n");

            foreach (var v in vehicles)
            {
                v.ShowDetails();
                Console.WriteLine("-----------------------------");
            }

            Console.ReadLine();
        }
    }
}

```
