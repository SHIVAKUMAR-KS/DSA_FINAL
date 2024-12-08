# Example :

Input: nums1 = [[1,2],[2,3],[4,5]], nums2 = [[1,4],[3,2],[4,1]]
Output: [[1,6],[2,3],[3,2],[4,6]]
Explanation: The resulting array contains the following:
- id = 1, the value of this id is 2 + 4 = 6.
- id = 2, the value of this id is 3.
- id = 3, the value of this id is 2.
- id = 4, the value of this id is 5 + 1 = 6.


Example 2:

Input: nums1 = [[2,4],[3,6],[5,5]], nums2 = [[1,3],[4,3]]
Output: [[1,3],[2,4],[3,6],[4,3],[5,5]]
Explanation: There are no common ids, so we just include each id with its value in the resulting list.


----------------------------------------------------------------
#Solution
```
class Solution {
    public int[][] mergeArrays(int[][] nums1, int[][] nums2) {
        ArrayList<ArrayList<Integer>> set = new ArrayList<>();
        int i=0, j=0;

        while(i<nums1.length || j<nums2.length){
            ArrayList<Integer> s = new ArrayList<>();
            if(i<nums1.length && j<nums2.length && nums1[i][0]==nums2[j][0]){
                s.add(nums1[i][0]);
                s.add(nums1[i][1]+nums2[j][1]);
                i++; j++;
                set.add(s);
            } else if(i<nums1.length && (j>=nums2.length || nums1[i][0]<nums2[j][0])){
                s.add(nums1[i][0]);
                s.add(nums1[i][1]);
                set.add(s);
                i++;
            } else if(j<nums2.length){
                s.add(nums2[j][0]);
                s.add(nums2[j][1]);
                set.add(s);
                j++; 
            }
        }

        int [][] arr = new int[set.size()][set.get(0).size()];
        for(int x=0; x<set.size(); x++){
            for(int y=0; y<set.get(0).size(); y++){
                arr[x][y] = set.get(x).get(y);
            }
        }
        return arr;
    }
}
```