# step1'

## memo
lowercaseのアルファベットだけなので、長さが26の配列をカウンタに用いれば各単語にどのアルファベットが
いくつあるか管理できそう。カウンタから可変長の配列にMapしておけば、最終的にvaluesを返せば良い

または、各単語をsortすればanagramに関しては同じ文字列になる。

## code
改善版はstep2.mdにあります

```java

class Solution {
    public List<List<String>> groupAnagrams(String[] strs) {
        Map<List<Integer>, List<String>> counterToWordList = new HashMap<>();
        for (int i=0; i<strs.length; i++) {
            int[] counter = new int[26];
            String word = strs[i];
            for (int j=0; j<word.length(); j++) {
                counter[word.charAt(j) - 'a'] ++;
            }

            List<Integer> key = new ArrayList<>();
            for(int count: counter) {
                key.add(count);
            }
            if (counterToWordList.containsKey(key)) {
                counterToWordList.get(key).add(word);
            } else {
                List<String> list = new ArrayList<>();
                list.add(word);
                counterToWordList.put(key, list);
            }
        }
        return new ArrayList<>(counterToWordList.values());
    }
}
```