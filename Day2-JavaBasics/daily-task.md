# Daily task (Day 2)

- Prime number between a given number
- City list creation and find by city name
- Random password generator

```java
import java.util.ArrayList;
import java.util.Arrays;
import java.util.Random;
import java.util.Scanner;

public class JavaBasic {

    // ---------------  Random Password Generator  -------------------

    public static String randomPasswordGenerator(int len){
        String arr = new String();
        Random random = new Random();

        String setOfChar = "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789!@_";

        while(len > 0){
            int randomIndex = random.nextInt(setOfChar.length());
            char ch = setOfChar.charAt(randomIndex);
            arr += ch;
            len--;
        }


        return arr;
    }
    // ---------------  City List  -------------------

    public static void findCityByName(String cityName){
        // contains, indexOf
        ArrayList<String> cities = new ArrayList();
        cities.add("Dhaka");
        cities.add("Khulna");
        cities.add("Comilla");
        cities.add("Bandorban");

        int index = cities.indexOf(cityName);
        if(index != -1){
            System.out.println("City " +cityName+ " found at "+ index);
        }else{
            System.out.println("City " +cityName+ " not found!");
        }

    }


    // ---------------  Prime Number  ---------------

    public static boolean[] primeFinder(int n){
        boolean [] primeNumbers = new boolean[n+1];
        Arrays.fill(primeNumbers, true);

        for(int i=2; i * i <= n; i++){
            if(primeNumbers[i] == true){
                for(int j= i * i; j<=n; j+=i){
                    primeNumbers[j] = false;
                }
            }
        }
        return primeNumbers;
    }

    public static void printPrime(boolean result[]){
        System.out.println("Prime numbers are" );
        for(int i=2; i<result.length; i++){
            if(result[i] == true){
                System.out.println("Number " +i+ " is prime");
            }
        }
    }

    public static void main(String[] args) {
        System.out.println("Please enter the range for Prime number");
        Scanner inputObj = new Scanner(System.in);
        boolean result[] = primeFinder(inputObj.nextInt());

        printPrime(result);

        findCityByName("Dhaka");
        System.out.println("\nPassword : "+randomPasswordGenerator(10));
    }
}

```