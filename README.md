# Password-Genrator
import java.util.Random;
import java.util.Scanner;
public class PasswordGenerator {
 public static void main(String[] args) {
 Scanner scanner = new Scanner(System.in);
 System.out.print("Enter the total length of the password: ");
 int length = scanner.nextInt();
 System.out.print("Enter the number of special characters to include: ");
 int specialCharCount = scanner.nextInt();
 if (specialCharCount > length) {
 System.out.println("Error: The number of special characters cannot exceed the total 
password length.");
 } else {
 String password = generatePassword(length, specialCharCount);
 System.out.println("Generated Password: " + password);
 }
 }
 private static String generatePassword(int length, int specialCharCount) {
 String upperCase = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
 String lowerCase = "abcdefghijklmnopqrstuvwxyz";
 String numbers = "0123456789";
 String specialChars = "!@#$%^&*()-_=+<>?/";
 String allChars = upperCase + lowerCase + numbers;
 Random random = new Random();
 StringBuilder password = new StringBuilder();
 for (int i = 0; i < specialCharCount; i++) {
 password.append(specialChars.charAt(random.nextInt(specialChars.length())));
 }
 for (int i = specialCharCount; i < length; i++) {
 password.append(allChars.charAt(random.nextInt(allChars.length())));
 }
 return shuffleString(password.toString());
 }
 private static String shuffleString(String input) {
 char[] characters = input.toCharArray();
 Random random = new Random();
 for (int i = 0; i < characters.length; i++) {
 int j = random.nextInt(characters.length);
 char temp = characters[i];
 characters[i] = characters[j];
 characters[j] = temp;
 }
 return new String(characters);
 }
}
