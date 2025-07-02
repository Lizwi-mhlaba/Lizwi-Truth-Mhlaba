package BMICalculator;
import java.util.Scanner;
import java.util.Locale;
public class BMICalculator {
public static void main(String[] args) {
Scanner scanner = new Scanner(System.in);
scanner.useLocale(Locale.US);
char repeat;
do {
// All our code
int unitChoice = getUnitChoice(scanner);
double weight = (unitChoice == 1) ? getValidInput(scanner, "Enter your weight in 
kilograms: ", 10, 600)
: getValidInput(scanner, "Enter your weight in pounds", 22, 1300);
double height = (unitChoice == 1)? getValidInput(scanner, "Enter your height in 
meters:",
0.5, 2.5)
:getValidInput(scanner, "Enter your height in inches", 20, 100);
double bmi= calculateBMI(unitChoice, weight, height);
System.out.println("Your BMI is " + bmi);
displayCategory(bmi);
repeat = askToRepeat(scanner);
} while (repeat == 'y' || repeat == 'Y');
scanner.close();
}
//Unit - Metric and Imperial
public static int getUnitChoice(Scanner scanner) {
int choice;
while(true) {
System.out.println("Select a preferred unit:\n"
+ "1.Metric (kg, m)\n"
+ "2.Imperial (lbs, in)\n"
+ "Please select either option 1 or option 2");
if(scanner.hasNextInt()) {
choice = scanner.nextInt();
if(choice == 1 || choice == 2) {
break;
}else {
System.out.println("Invalid choice. Please enter either 1 or 2");
}
} else {
System.out.println("Invalid input. Please enter a number 1 or 2");
scanner.next();
}
}
return choice;
}
public static double getValidInput(Scanner scanner, String prompt, double min,
double max) {
double value;
while(true) {
System.out.println(prompt);
if(scanner.hasNextDouble()){
value = scanner.nextDouble();
if(value >= min && value <= max) {
//the code will run the value greater or equal to minimum AND value less or 
equal to maximum.
break;
} else {
System.out.printf("Please enter a value between %.1f and %.1f.\n", min, max);
}
} else {
System.out.println("Invalid input. Please enter a value");
scanner.next();
}
}
return value;
}
public static double calculateBMI(int unitChoice, double weight, double height) {
double totalBMI;
if(unitChoice == 1) {
totalBMI = (weight / height * height);
} else {
totalBMI = (703 * weight) / (height / height);
}
return totalBMI;
}
public static void displayCategory(double bmi) {
if(bmi<16.0) {
System.out.println("Severely Underweight");
} else if(bmi<18.5) {
System.out.println("Underweight");
}else if(bmi<25.0) {
System.out.println("Normal");
}else if(bmi<30.0){
System.out.println("Overweight");
}else if(bmi<35.0) {
System.out.println("Obese");
}else if(bmi<40.0) {
System.out.println("Severely Obese");
}else {
System.out.println("Morbidly Obese");
} //either system will print or display the BMI weight
}
public static char askToRepeat(Scanner scanner) {
while(true) {
System.out.println("Do you want to calculate your BMI again?");
String input = scanner.next().trim().toLowerCase();
if(input.equals("y") || input.equals("n")) {
return 'y';
}else if(input.equals("n")) {
return 'n';
} else {
System.out.println("Invalid input.Please enter either y or n");
 }
 }
}
public static char askToRepeat1(Scanner scanner) {
while(true) {
System.out.println("Do you want to run the program again? (Y/y to continue, 
N/n to stop):");
String input = scanner.next().trim().toLowerCase();
if(input.equals("y")){
return 'y';
} else if(input.equals("n")){
return 'n';
}else {
System.out.println("Invalid input.Please enter Y/y or N/n.");
}
}
 }
}//end class
