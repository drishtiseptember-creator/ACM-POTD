```
void moveZeroes(int* nums, int numsSize) {
    int a;
    for(int i=0;i<numsSize;i++){
        for(int j=0;j<numsSize-i-1;j++){
            if(nums[j]==0){
                a=nums[j];
                nums[j]=nums[j+1];
                nums[j+1]=a;
            }
        }
    }
}
```