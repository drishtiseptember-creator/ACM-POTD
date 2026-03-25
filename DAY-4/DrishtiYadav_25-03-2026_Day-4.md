```
int missingNumber(int* nums, int numsSize) {
int a,k;
for(int i=0;i<numsSize-1;i++){
    for(int j=0;j<numsSize-i-1;j++){
        if(nums[j+1]<nums[j]){
        a=nums[j];
        nums[j]=nums[j+1];
        nums[j+1]=a;
        }
    }
}    
for(k=0;k<numsSize;k++){
    if(nums[k]!=k){
        break;
    }
}
return k;
}
```