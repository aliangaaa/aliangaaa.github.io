最长递增(=)子序列的长度

n2

```cpp
int calMaxLen(vector<int> nums) {
	int len = nums.size();
	int ans = 0;
	vector<int> dp(len, 1);
	for(int i = 0; i < len; i++) {
		for(int j = 0; j < i; j++) {
			if(nums[j] <= nums[i]) {
				dp[i] = max(dp[j] + 1, dp[i]);
			}
		}
		ans = max(ans, dp[i]);
	}
	return ans;
}
```

nlog(n) 耐心排序

```cpp
int calMaxLen(vector<int> nums) {
	int len = nums.size();
	vector<int> top(len);
	int piles = 0;
	for(int i = 0; i < len; i++) {
		int poker = nums[i];
		int l = 0, r = piles;
		while(l < r) {
			int mid = l + r >> 1;
			if(top[mid] > poker)	r = mid;
			else l = mid + 1;
		}
		if(poker >= top[l]) {
			piles++;
		}
		top[l] = poker;
	}
	return piles;
}
```

递增(=)子序列的最大和 &#x20;

```cpp
int sumMaxLen(vector<int> nums) {
	int len = nums.size();
	int ans = 0;
	vector<int> dp(len, 1);
	for(int i = 0; i < len; i++) {
		dp[i] = nums[i];
		for(int j = 0; j < i; j++) {
			if(nums[j] <= nums[i]) {
				dp[i] = max(dp[j] + nums[i], dp[i]);
			}
		}
		ans = max(ans, dp[i]);
	}
	return ans;
}
```

