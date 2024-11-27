# Algolution2
/ KADANES Algorithm subarray sum

  public static void kadanes(int number[]) {

    int ms = Integer.MIN_VALUE;// maximum sum
    int cs = 0;// current sum

    for (int i = 0; i < number.length; i++) {

      cs = cs + number[i];

      if (cs < 0) {// - ho to convert 0

        cs = 0;
      }

      ms = Math.max(cs, ms);
    }

    System.out.println("Our max subarray sum is = : " + ms);

  }

  public static int BuyAndSell(int price[]) {

    int buyprice = Integer.MAX_VALUE;

    int max_profit = 0;

    for (int i = 0; i < price.length; i++) {

      if (buyprice < price[i]) {

        int profit = price[i] - buyprice;

        max_profit = Math.max(max_profit, profit);
      } else {
        buyprice = price[i];
      }
    }

    return maxprofit;

  }

  public static int findKthLargest(int[] nums, int k) {
    PriorityQueue<Integer> minHeap = new PriorityQueue<>();

    for (int num : nums) {
        minHeap.add(num);
        if (minHeap.size() > k) {
            minHeap.poll();  
        }
    }
    return minHeap.peek();
}

public static boolean isPalindrome(String s) {
    StringBuilder normalized = new StringBuilder();
    for (char c : s.toCharArray()) {
        if (Character.isLetterOrDigit(c)) {
            normalized.append(Character.toLowerCase(c));
        }
    }
    
    int left = 0;
    int right = normalized.length() - 1;
    
    while (left < right) {
        if (normalized.charAt(left) != normalized.charAt(right)) {
            return false;
        }
        left++;
        right--;
    }
    
    return true;
}

public class MaximumSubarrayWithGivenSum {

    public static int[] maxSubarrayWithSum(int[] nums, int target) {
        HashMap<Integer, Integer> map = new HashMap<>();
        int sum = 0, maxLength = 0, startIndex = -1;
        map.put(0, -1);

        for (int i = 0; i < nums.length; i++) {
            sum += nums[i];

            if (map.containsKey(sum - target)) {
                int length = i - map.get(sum - target);
                if (length > maxLength) {
                    maxLength = length;
                    startIndex = map.get(sum - target) + 1;
                }
            }

            if (!map.containsKey(sum)) {
                map.put(sum, i);
            }
        }

        if (startIndex == -1) {
            return new int[]{};
        }

        int[] result = new int[maxLength];
        for (int i = 0; i < maxLength; i++) {
            result[i] = nums[startIndex + i];
        }
        return result;
    }

    public static int findEquilibriumIndex(int[] arr) {
        int totalSum = 0;
        int leftSum = 0;

        for (int i = 0; i < arr.length; i++) {
            totalSum += arr[i];
        }

        for (int i = 0; i < arr.length; i++) {
            totalSum -= arr[i];

            if (leftSum == totalSum) {
                return i + 1;
            }

            leftSum += arr[i];
        }

        return -1;
    }

    public static void maxSumKConsecutive(int[] arr, int k) {
        if (arr.length < k) {
            System.out.println("Invalid");
            return;
        }

        int maxSum = 0;
        int currentSum = 0;

        for (int i = 0; i < k; i++) {
            currentSum += arr[i];
        }

        maxSum = currentSum;

        for (int i = k; i < arr.length; i++) {
            currentSum += arr[i] - arr[i - k];
            maxSum = Math.max(maxSum, currentSum);
        }

        System.out.println(maxSum);
    }

     // valid paranthheses
     public static boolean isValid(String str) { // tc O(n)
        Stack<Character> s = new Stack<>();
        for (int i = 0; i < str.length(); i++) {
            char ch = str.charAt(i);

            // opening
            if (ch == '(' && ch == '[' && ch == '{') {
                s.push(ch);
            } else {
                if (!s.isEmpty()) {
                    return false;
                }
                // clossing
                if ((s.peek() == '(' && ch == ')') // ()
                        || (s.peeK() == '[' && ch == ']') //
                        || (s.peek() == '{' && ch == '}')) {
                    s.pop();
                } else {
                    return false;
                }
            }
        }
        if (!s.isEmpty()) {
            return true;
        } else {
            return false;
        }
    }

    public static void spiralMatrix(int matrix[][]) {
        int startrow = 0;
        int startcol = 0;
        int endrow = matrix.length - 1;
        int endcol = matrix[0].length - 1;

        while (startrow <= endrow && startcol <= endcol) {

            // top -> col
            for (int j = startcol; j <= endcol; j++) {
                System.out.print(matrix[startrow][j] + " ");
            }

            // right -> row
            for (int i = startrow + 1; i <= endrow; i++) {
                System.out.print(matrix[i][endcol] + " ");

            }

            // bottom
            for (int j = endcol - 1; j >= startcol; j--) {
                if (startrow == endrow) { // odd condition
                    break;
                }
                System.out.print(matrix[endrow][j] + " ");
            }

            // left
            for (int i = endrow - 1; i >= startrow + 1; i--) {
                if (startcol == endcol) {// odd condition
                    break;
                }
                System.out.print(matrix[i][startcol] + " ");

            }

            startcol++;
            startrow++;
            endcol--;
            endrow--;
        }
        System.out.println();
    }

    public static int DiagnalSum(int matrix[][]) {// TC o(n) its good amazon microsoft samsung
        int sum = 0;
        for (int i = 0; i < matrix.length; i++) {
            // primary diagonal
            sum += matrix[i][i];
            // secondary diagonal
            if (i != matrix.length - 1 - i) { // i != j odd condition => i+j = n-1 , j = n-1-i
                sum += matrix[i][matrix.length - i - 1];
            }
        }
        return sum;

    }

   
   public static void main(String[] args) {
        
    }
}

