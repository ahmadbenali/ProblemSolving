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
