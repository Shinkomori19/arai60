# step2

## 変更点

- 拡張for文の使用
- word.toCharArray()の使用

## code

```java
class Solution {
    public List<List<String>> groupAnagrams(String[] strs) {
        Map<String, List<String>> anagramMap = new HashMap<>();
        for (String word : strs) {
            int[] counter = new int[26];
            for (char c : word.toCharArray()) {
                counter[c - 'a']++;
            }

            StringBuilder keyBuilder = new StringBuilder();
            for (int count : counter) {
                keyBuilder.append('#').append(count);
            }
            String key = keyBuilder.toString();

            anagramMap.computeIfAbsent(key, k -> new ArrayList<>()).add(word);
        }
        return new ArrayList<>(anagramMap.values());
    }
}

```