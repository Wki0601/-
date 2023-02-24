#include <stdio.h>


void findlength(int* nums1, int nums1Size, int* nums2, int nums2Size) {

	int max = 0, maxi = 0;
	
	int num[1005][105] = { 0 };
	
	for (int i = 1;i <= nums2Size;i++) {
	
		for (int j = 1;j <= nums1Size;j++) {
		
			if (j == 1) {
			
				if (nums1[i] == nums2[j]) num[i][j] = 1;
				
				else num[i][j] = 0;
				
			}
			
			else {
			
				if (nums1[i] == nums2[j]) num[i][j] = 1 + num[i - 1][j - 1];
				
				else num[i][j] = 0;
				
			}
			
			if (max <= num[i][j]) {
			
				max = num[i][j];
				
				maxi = i;
				
			}
			
		}
		
	}
	
	printf("%d\n", max);
	
	for (int i = max - 1;i >= 0;i--) {
	
		printf("%d ", nums1[maxi - i]);
		
	}
	
	printf("\n");
	
}


int main() {

	char ch;
	
	int nums1[1000], nums2[100];
	
	int max = 0, ans = 0, temp1 = 0, temp2 = 0;
	
	printf("请输入nums1：");
	
	while (ch = getchar()) {
	
		if (ch == '\n') break;
		
		if (ch >= '0' && ch <= '9') {
		
			ans = ans * 10 + (ch - '0');
			
		}
		
		else {
		
			if (ans != 0) {
			
				nums1[++temp1] = ans;
				
				ans = 0;
				
			}
			
		}
		
	}
	
	printf("请输入nums2：");
	
	while (ch = getchar()) {
	
		if (ch == '\n') break;
		
		if (ch >= '0' && ch <= '9') {
		
			ans = ans * 10 + (ch - '0');
			
		}
		
		else {
		
			if (ans != 0) {
			
				nums2[++temp2] = ans;
				
				ans = 0;
				
			}
			
		}
		
	}
	
	printf("输入完毕。\n");
	
	findlength(nums1, temp1, nums2, temp2);
	
	return 0;
	
}

