# step2

## 変更点

- seenValToIndexを、seenNumToIndexに改名
- diffを、complementに改名

```java

class Solution {
    public int[] twoSum(int[] nums, int target) {
        Map<Integer, Integer> seenNumToIndex = new HashMap<>();
        for (int i=0; i < nums.length; i++) {
            int complement = target - nums[i];
            if (seenNumToIndex.containsKey(complement)) {
                return new int[]{i, seenNumToIndex.get(complement)};
            }
            seenNumToIndex.put(nums[i], i);
        }
        return new int[]{};
    }
}

```