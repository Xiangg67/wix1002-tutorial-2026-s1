import java.util.Random;

// WIX1002 Tutorial 6 - Question 1 (a) to (h)
class Tutorial6Q1 {

            // (a) Return the maximum of 3 integers
            public static int max(int a, int b, int c) {
                int largest = a;
                if (b > largest) largest = b;
                if (c > largest) largest = c;
                return largest;
            }

            // (b) Check whether n is a square number (0, 1, 4, 9, 16, ...)
            public static boolean isSquare(int n) {
                if (n < 0) return false;
                int root = (int) Math.sqrt(n);
                return root * root == n;
            }

            // (c) C(n,k) = n! / (k! (n-k)!)
            // Helper method: factorial. long holds factorials up to 20! only.
            public static long factorial(int n) {
                long result = 1;
                for (int i = 2; i <= n; i++) {
                    result *= i;
                }
                return result;
            }

            public static long combination(int n, int k) {
                if (k < 0 || k > n) return 0;
                return factorial(n) / (factorial(k) * factorial(n - k));
            }

            // (d) Check whether n is a pentagonal number: Pi = i(3i - 1) / 2
            // Pentagonal numbers: 1, 5, 12, 22, 35, ...
            public static boolean isPentagonal(int n) {
                int i = 1;
                int p = 1;
                while (p <= n) {
                    if (p == n) return true;
                    i++;
                    p = i * (3 * i - 1) / 2;
                }
                return false;
            }

            // (e) Display the number of letters and digits in a String
            public static void countLettersDigits(String s) {
                int letters = 0;
                int digits = 0;
                for (int i = 0; i < s.length(); i++) {
                    char ch = s.charAt(i);
                    if (Character.isLetter(ch)) {
                        letters++;
                    } else if (Character.isDigit(ch)) {
                        digits++;
                    }
                }
                System.out.println("Letters: " + letters);
                System.out.println("Digits : " + digits);
            }

            // (f) Fill the array parameter with 10 random numbers (0 to 100).
            // The method is void, but main can still see the numbers because an
            // array parameter refers to the SAME array that main created.
            public static void generateRandom(int[] numbers) {
                Random r = new Random();
                for (int i = 0; i < numbers.length; i++) {
                    numbers[i] = r.nextInt(101);   // 0 to 100 inclusive
                }
            }

            // (g) A void method cannot use return, so the two results are
            // "returned" by storing them in an array parameter:
            // result[0] = area, result[1] = circumference
            public static void circle(double radius, double[] result) {
                result[0] = Math.PI * radius * radius;
                result[1] = 2 * Math.PI * radius;
            }

            // (h) Keep generating random numbers from 0 to 10 and return the
            // first number that has already appeared before.
            public static int firstRepeated() {
                Random r = new Random();
                boolean[] seen = new boolean[11];   // seen[x] is true once x appears
                System.out.print("Generated: ");
                while (true) {
                    int num = r.nextInt(11);         // 0 to 10 inclusive
                    System.out.print(num + " ");
                    if (seen[num]) {
                        System.out.println();
                        return num;
                    }
                    seen[num] = true;
                }
            }

            public static void main(String[] args) {
                System.out.println("(a) max(7, 19, 4) = " + max(7, 19, 4));

                System.out.println("(b) isSquare(49) = " + isSquare(49));
                System.out.println("    isSquare(50) = " + isSquare(50));

                System.out.println("(c) C(5, 2) = " + combination(5, 2));
                System.out.println("    C(10, 3) = " + combination(10, 3));

                System.out.println("(d) isPentagonal(22) = " + isPentagonal(22));
                System.out.println("    isPentagonal(23) = " + isPentagonal(23));

                System.out.println("(e) \"WIX1002 Java 2020\"");
                countLettersDigits("WIX1002 Java 2020");

                int[] numbers = new int[10];
                generateRandom(numbers);
                System.out.print("(f) Random numbers: ");
                for (int n : numbers) {
                    System.out.print(n + " ");
                }
                System.out.println();

                double[] result = new double[2];
                circle(3.0, result);
                System.out.printf("(g) radius 3.0 -> Area = %.2f, Circumference = %.2f%n",
                        result[0], result[1]);

                System.out.println("(h)");
                int repeated = firstRepeated();
                System.out.println("    First number generated twice: " + repeated);
            }
        }