# RomanToInt
Problem Is Solved By Creating A HashMap

import java.util.HashMap;

public class RomanToInteger {
    public static int romanToInt(String s) {
        // Creation of  HashMap to store Roman numbers and their corresponding integer values
        HashMap<Character, Integer> romanMap = new HashMap<>();
        romanMap.put('I', 1);
        romanMap.put('V', 5);
        romanMap.put('X', 10);
        romanMap.put('L', 50);
        romanMap.put('C', 100);
        romanMap.put('D', 500);
        romanMap.put('M', 1000);

        int total = 0; // Initialize total to store the result
        int prevValue = 0; // Initialize previous value to handle subtraction cases

        // Traverse the Roman numbers string from right to left
        for (int i = s.length() - 1; i >= 0; i--) {
            char currentChar = s.charAt(i);
            int currentValue = romanMap.get(currentChar);

            // If the current value is less than the previous value, subtract it
            if (currentValue < prevValue) {
                total -= currentValue;
            } else {
                total += currentValue; //orelse add it
            }

            // Update the previous value for the next iteration
            prevValue = currentValue;
        }

        return total; // Return the total as the result
    }

    public static void main(String[] args) {
        // Test cases
        String roman1 = "III";
        String roman2 = "LVIII";
        String roman3 = "MCMXCIV";

        System.out.println(roman1 + " -> " + romanToInt(roman1)); 
        System.out.println(roman2 + " -> " + romanToInt(roman2)); 
        System.out.println(roman3 + " -> " + romanToInt(roman3));
    }
}


