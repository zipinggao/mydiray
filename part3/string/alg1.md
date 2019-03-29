##题目描述

给定一个字符串，请你找出其中不含有重复字符的 最长子串 的长度。

##示例：
输入: "abcabcbb"

输出: 3 

解释: 因为无重复字符的最长子串是 "abc"，所以其长度为 3。 

##题解： 
方案一

            class Solution {
                public boolean charUnique(String s,int start,int end){
                    Set<Character> set = new HashSet<>();
                    for(int i = start;i<end;i++){
                        Character ch = s.charAt(i);
                        if(set.contains(ch)) return false;
                        set.add(ch);
                    }
                    return true;
                } 
            
                
                public int lengthOfLongestSubstring(String s) {
                    int len = s.length();
                    int max_len = 0;
                    for (int i = 0 ;i < len;i++){
                        for(int j = i+1; j<=len; j++){
                            if(charUnique(s,i,j)) max_len = Math.max(max_len,j-i);                    
                        }
                    }
                    return max_len;
                }
            }
            
            
方案二

            class Solution {
            
            public int lengthOfLongestSubstring(String s) {
                int len = s.length();
                Set<Character> set = new HashSet<>();
                int add_w = 0,sub_w = 0;
                int max_len = 0;
                while(add_w < len && sub_w < len){
                    if(!set.contains(s.charAt(add_w))){
                        set.add(s.charAt(add_w++));
                        max_len = Math.max(max_len,add_w-sub_w);
                    }else{
                        set.remove(sub_w++);
                    }
                }
                return max_len;
            }
        }
        

方案三
        
        public class Solution {
            public int lengthOfLongestSubstring(String s) {
                int n = s.length(), ans = 0;
                Map<Character, Integer> map = new HashMap<>(); // current index of character
                // try to extend the range [i, j]
                for (int j = 0, i = 0; j < n; j++) {
                    if (map.containsKey(s.charAt(j))) {
                        i = Math.max(map.get(s.charAt(j)), i);
                    }
                    ans = Math.max(ans, j - i + 1);
                    map.put(s.charAt(j), j + 1);
                }
                return ans;
            }
        }
        
方案四
   
        class Solution {
            public int lengthOfLongestSubstring(String s) {
                int n = s.length();
                int ans = 0;
                int [] index = new int [128];
                for (int j = 0,i=0;j<n;j++){
                    i =Math.max(index[s.charAt(j)],i);
                    ans = Math.max(ans,j-i+1);
                    index[s.charAt(j)] = j+1;
                }
                return ans;
                }
        }