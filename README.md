# daily-practice

Palindrome Number------------------------------------------------------------------------------------------------------

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


2. Two Sum -----------------------------------------------------------------------------------------------------------


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

2. Roman to integer --------------------------------- using hashmap ---------------------------------------------------------------
   
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
