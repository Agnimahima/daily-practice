# daily-practice

1-Palindrome Number------------------------------------------------------------------------------------------------------

class Solution {
    
     public boolean isPalindrome(int x) {
        if(x<0)
        { return false;
        }
    
    long reversed=0 ;
    long temp = x ;

     while(temp!=0){
        int digit= (int) (temp % 10);
        reversed=reversed*10+digit;
        temp/=10;
     }      
     return (reversed==x);
    }
};

2- Two Sum -----------------------------------------------------------------------------------------------------------

class Solution {


    public int[] twoSum(int[] nums, int target) {
        int targetarray[] = new int[2];
         
        for(int i=0;i<nums.length;i++)
        {  
             for(int j=1;j<nums.length;j++)
             {
                 if(nums[i]+nums[j]==target && i!=j)
                 {
                   targetarray[0]=i;
                    targetarray[1]=j;
                     
                 }
             }

        }
        return targetarray;
    }
}

3- Roman to integer --------------------------------- using hashmap ---------------------------------------------------------------

   
class Solution {
   
    public int romanToInt(String s) {
     
        Map<Character,Integer>m = new HashMap<>();
        m.put('I',1);
        m.put('V',5);
        m.put('X',10);
        m.put('L',50);
        m.put('C',100);
        m.put('D',500);
        m.put('M',1000);
        
        int num=0;
        for(int i=0;i<s.length();i++){
            if( i< s.length()-1 && m.get(s.charAt(i))< m.get(s.charAt(i+1)) )
            {
                num -= m.get(s.charAt(i));
            }
            else
            {
                num += m.get(s.charAt(i)); 
            }
        } 
  
        return num;
    }
}

4- Longest Common Prefix ------------------------------------------------------------------------------------------

   
class Solution {

    public String longestCommonPrefix(String[] strs) {
    
        if (strs == null || strs.length == 0)
            return "";
            
        String prefix = strs[0];
        
        for (String s : strs)
            while (s.indexOf(prefix) != 0)
                prefix = prefix.substring(0, prefix.length() - 1);
        return prefix;
    }
}


5- Valid Parentheses-------------------------------------------------------------------------------------------------

public class Solution {

    public static boolean isValid(String s) {
        while (true) {
            if (s.contains("()")) {
                s = s.replace("()", "");
            } else if (s.contains("{}")) {
                s = s.replace("{}", "");
            } else if (s.contains("[]")) {
                s = s.replace("[]", "");
            } else {
                // If the string becomes empty, it indicates all brackets are matched.
                return s.isEmpty();
            }
        }
    }
}

class Solution {

    public boolean isValid(String s) {
    
      Stack<Character> stack = new Stack<Character>();
        // create an empty stack
      for (char c : s.toCharArray()) {
            if (c == '(') 
                stack.push(')'); 
            else if (c == '{') 
                stack.push('}'); 
            else if (c == '[')
                stack.push(']');  
            else if (stack.isEmpty() || stack.pop() != c) // if the character is a closing bracket
                return false;
        }
        return stack.isEmpty();
    }
}

 6- Merging two sorted list-----------------------------------------------------------------------------------------------

 /**
 Merge two sorted linked lists and return it as a new list. The new list should be made by
 splicing together the nodes of the first two lists.
 */
public class Main {

       public static ListNode mergeTwoLists(ListNode n1, ListNode n2) {
        if(n1==null)
         return n2;                  //main logic
        if(n2==null)
         return n1; 
    
       if(n1.val <= n2.val){
        n1.next= mergeTwoLists(n1.next,n2);
         return n1;
       }    
        else{
          n2.next= mergeTwoLists(n1,n2.next);
          return n2;
       }      
          
    }
    public static void main(String[] args){
        ListNode n1 = new ListNode(1);
        ListNode n11 = new ListNode(2);
        ListNode n111 = new ListNode(4);
        n1.next = n11;
        n11.next = n111;
        ListNode n2 = new ListNode(1);
        ListNode n22 = new ListNode(3);
        ListNode n222 = new ListNode(4);
        n2.next = n22;
        n22.next = n222;

        ListNode node = mergeTwoLists(n1, n2);
        printListValues(node);
    }
    private static void printListValues(ListNode node) {
        while(node!=null){
            System.out.print(node.val);
            if(node.next!=null){
                System.out.print("->");
            }
            node = node.next;
        }
    }
    public static class ListNode {
        int val;
        ListNode next;
        ListNode(int x) { val = x; }
    }
}   

7- Remove Duplicates from Sorted Array-----------------------------------------------------------------------------------

Input: nums = [0,0,1,1,1,2,2,3,3,4]
Output: nums = [0,1,2,3,4,_,_,_,_,_]

class Solution {

    public int removeDuplicates(int[] nums) {       
       if(nums.length==0)
         return 0;
        else
         {   int c=0;
             for(int i=1;i<nums.length;i++)
             {
                 if(nums[c]!=nums[i])
                 {
                     nums[++c]=nums[i];
                 }
             } 
             return c+1;
         } 
  }
}


 8- Remove Element -----------------------------------------------------------------------------------------------------

 Input: nums = [3,2,2,3], val = 3
 Output: 2, nums = [2,2,_,_]

 class Solution {
 
    public int removeElement(int[] nums, int val)
    {  int index=0;
    for(int i=0;i<nums.length;i++){
        if(nums[i]!=val){
            nums[index]=nums[i];
            index++;
        }
    }
         return index;
        

    }
}

9- Find the Index of the First Occurrence in a String---------------------------------------------------------------------

class Solution {

    public int strStr(String haystack, String needle) {
         int index= haystack.indexOf(needle);
         return index;
    }
}

class Solution {

    public int strStr(String haystack, String needle) {
        for(int i = 0, j = needle.length(); j<=haystack.length(); i++,j++){
            if(haystack.substring(i,j).equals(needle)){
                return i;
            }
        }
        return -1;
    }

 class Solution {
    /** this is the first kmp algorithm */
    public int strStr(String haystack, String needle) {
        int i =0;
        char[] haystackCharArray = haystack.toCharArray();
        char[] needleCharArray = needle.toCharArray();
        for (i = 0; i <= haystackCharArray.length - needleCharArray.length; i++) { 
            boolean match = true;
            for (int j = 0; j < needleCharArray.length; j++) {
                if (haystackCharArray[i + j] != needleCharArray[j]) {
                    match = false;
                    break;
                }
            }
            if (match) {
                return i;
            }
        }
        return -1;
    }
}   


class Solution {

    public int searchInsert(int[] nums, int target) {
        int index=nums.length;
       for(int i=0;i<nums.length;i++){
            if(nums[i] == target)
               return i;
       }
       //except for [1] it executes well not optimal
       for(int i=0;i<nums.length-1;i++){
         if(nums[i]<=target && target <= nums[i+1])
               return i+1;
       } 
        return index;
    }
}
}
