# ProblemSolving
here i put my thoughts of solving problems with brute force and then with optimize solution 



## two sum
see my thoughts on tablet.
### brute force
```
public int[] twoSum(int[] nums, int target) {
        int len=nums.length;

        for(int i=0;i<len;i++)
        {
            int y = target - nums[i];

            for(int j=0;j<len;j++)
            {
                if(j==i) continue;
                else
                {
                    if(nums[j]+nums[i]==target)
                    return new int[] {i,j};
                }
            }
        }
        return new int[] {};

    }
```
> [!NOTE]
> RunTime = 91ms , Memory = 46.90 MB

### HashMap solution
```
 public int[] twoSum(int[] nums, int target) {
        int len=nums.length;

       Map<Integer,Integer> map=new HashMap<>();

       for(int i=0;i<len;i++)
       {
        int y = target-nums[i];

        if(map.containsKey(y)) return new int[] {map.get(y),i};

        map.put(nums[i],i);
       }

       return new int[] {};
    }
```
> [!NOTE]
> RunTime = 2ms , Memory = 47.14

## Longest common prefix 
see my thoughts on tablet.
### Brute force
```
public String longestCommonPrefix(String[] strs) {

        if (strs == null || strs.length == 0) return "";

        int len=strs[0].length();

        for(int i=0;i<len;i++)
        {
            char c=strs[0].charAt(i);

            for(int j=1;j<strs.length;j++)
            {
                if(i == strs[j].length() || strs[j].charAt(i) != c)
                return strs[0].substring(0,i);
            }
        }

        return strs[0];
        
    }
```

## Best time to buy and sell stock
see my thoughts on tablet.

### Brute force
```
time limit public int maxProfit(int[] prices) {





int max=0;

int len=prices.length;



for(int buy=0;buy<len;buy++)

{

for(int sell=buy+1;sell<len;sell++)

{

if(buy<sell) max=Math.max(prices[sell]-prices[buy],max);

}

}



return max;

}
```
> [!NOTE]
> Time limit with nested loop . not good enought

### without nested loop
```
public int maxProfit(int[] prices) {


        int min=Integer.MAX_VALUE;
        int max=0;
        int len=prices.length;

        for(int i=0;i<len;i++)
        {
            if(prices[i]<min) min=prices[i];

            else if(max<prices[i]-min) max=prices[i]-min;
        }

        return max;
    }
```
> [!NOTE]
> perfect . RunTime = 1ms , Memory = 94 MB

## Valid Parentheses
You use a Stack because it follows the LIFO (Last-In, First-Out) principle, which is perfect for nested structures like parentheses

```
public boolean isValid(String s) {
        
        Stack<Character> stack=new Stack<>();

        for(char c:s.toCharArray())
        {
            if(c=='(' || c=='[' || c=='{') stack.push(c);
            else
            {
                //to check if there are open in s
                if(stack.isEmpty()) return false;

                char p=stack.pop();
                if(c==')' && p !='(') return false;
                if(c==']' && p !='[') return false;
                if(c=='}' && p !='{') return false;
                
            }
        }
        //return true; will not work if s = [ .
        return stack.isEmpty();
    }
```
