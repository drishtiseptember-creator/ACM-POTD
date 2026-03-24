
int maxProfit(int* prices, int pricesSize) {
    int smallest=prices[0];
    int profit=0;
    int maxprofit=0;
    for(int i=1;i<pricesSize;i++){
        profit=prices[i]-smallest;
        if(profit>maxprofit){
            maxprofit=profit;
        }
        if(prices[i]<smallest){
            smallest=prices[i];
        }
    }
    return maxprofit;
}
