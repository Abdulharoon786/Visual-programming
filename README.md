# Vp-lab-project-2-
Attributes program 

using System;

// Define a custom attribute
[AttributeUsage(AttributeTargets.Class | AttributeTargets.Method, AllowMultiple = false)]
public class DescriptionAttribute : Attribute
{
    public string Description { get; set; }

    public DescriptionAttribute(string description)
    {
        Description = description;
    }
}

// Apply the attribute to a class
[Description("This is a sample class")]
public class SampleClass
{
    // Apply the attribute to a method
    [Description("This is a sample method")]
    public void SampleMethod()
    {
        Console.WriteLine("Sample method executed");
    }
}

class Program
{
    static void Main()
    {
        // Get the attribute values
        var classAttribute = (DescriptionAttribute)Attribute.GetCustomAttribute(typeof(SampleClass), typeof(DescriptionAttribute));
        Console.WriteLine($"Class Description: {classAttribute.Description}");

        var methodAttribute = (DescriptionAttribute)Attribute.GetCustomAttribute(typeof(SampleClass).GetMethod("SampleMethod"), typeof(DescriptionAttribute));
        Console.WriteLine($"Method Description: {methodAttribute.Description}");

        // Create an instance of the class and call the method
        var sampleClass = new SampleClass();
        sampleClass.SampleMethod();
    }
}