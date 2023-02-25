# -Best-Time-to-Buy-and-Sell-Stock
Problem Statement
You are given an array prices where prices[i] denotes the price of a stock on the ith day. You want to maximize the profit by buying a stock and then selling it at a higher price.

Suppose you can make a single buy and single sell at any date after you buy, what is the maximum profit that you can make?

Note: Return 0 if you cannot make a profit.

Naive Approach
The simple solution is to check every possible pair and find the pair which gives maximum profit.

Analysis
Time Complexity: O(n2)
Auxiliary Space Complexity: O(1)
Implementation
C++
int maxProfit(vector<int> &prices) {
    int profit = 0;
	for(int i = 0; i < prices.size(); i++) {
		for(int j = i + 1; j < prices.size(); j++) {
			profit = max(profit, prices[j] - prices[i]);
		}
	}
	return profit;
}
Java
class Solution {
	int maxProfit(int[] prices) {
	    int profit = 0;
		for(int i = 0; i < prices.length; i++) {
			for(int j = i + 1; j < prices.length; j++) {
				profit = Math.max(profit, prices[j] - prices[i]);
			}
		}
		return profit;
	}
}
Optimal Approach
Traverse the given array and while traversing keep updating the minimum price. Also, keep updating the maximum difference between the current selling price and minimum price during the traversal to get the maximum profit.

Analysis
Time Complexity: O(n)
Auxiliary Space Complexity: O(1)
Implementation
C++
int maxProfit(vector<int> &prices) {
    int profit = 0, minPrice = INT_MAX;
	for(int i = 0; i < prices.size(); i++) {
		minPrice = min(minPrice, prices[i]);
		profit = max(profit, prices[i] - minPrice);
	}
	return profit;
}
Java
class Solution {
	int maxProfit(int[] prices) {
	    int profit = 0, minPrice = Integer.MAX_VALUE;
		for(int i = 0; i < prices.length; i++) {
			minPrice = Math.min(minPrice, prices[i]);
			profit = Math.max(profit, prices[i] - minPrice);
		}
		return profit;
	}
}
