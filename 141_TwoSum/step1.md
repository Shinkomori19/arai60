# step1

## memo

PythonでLeetCodeをやっていたときに解いた。
また、Google公式かなにかのCoding test動画で見たことがある。

浮かんだ解法は3つで、

- brute force. 時間計算量がO(N^2)になり、10^8ぐらいのサイズの配列を想定しないといけないのでしんどい。実装は簡単そう
- ソートしてtwo pointerで両端から探索。時間計算量はO(N * logN)に改善。実装も難しくなさそう。
実装を見るとArrays.sort()はQuick sort系を使っているみたいソートの空間計算量はO(1)になるので気にしないで良さそう
- 見たことのある数字をMapに持っておき(値をindexにマップする)、全数字を見る中でほしい値がMapの中に無いか確認。計算量はどちらもO(N)になりそう。

2つ目、3つ目のどちらが良いかはトレードオフで場合によりそうだが、今回は時間計算量が小さい3を採用

```java

class Solution {
    public int[] twoSum(int[] nums, int target) {
        Map<Integer, Integer> seenValToIndex = new HashMap<>();
        for (int i=0; i < nums.length; i++) {
            int diff = target - nums[i];
            if (seenValToIndex.containsKey(diff)) {
                return new int[]{i, seenValToIndex.get(diff)};
            }
            seenValToIndex.put(nums[i], i);
        }
        return new int[]{};
    }
}

```

## 感想
ロジックは浮かぶが、Javaに慣れておらず文法エラーが多発。早く慣れたい
