# 
```C++ runnable
#include <iostream>

using namespace std;

int selectk(int a[], int low, int high, int k)
{
    if (k<=0) return -1;
    if (k>(high-low+1)) return -1;
    int pivot = low+rand()%(high-low+1);
    swap(a[low],a[pivot]);
    int m = low;
    int count = 1;
    //move the larger number to the left of array
    for (int i = low+1; i<=high; ++i)
    {
        if(a[i] > a[low])
        {
            swap(a[++m],a[i]);
            count++;
        }
    }
    swap(a[m],a[low]);
    if (count > k)
    {
        return selectk(a,low,m-1,k);
    }
    else if (count < k)
    {
        return selectk(a,m+1,high,k-count);
    } 
    else 
    {
        return m;
    }
 }
 
 int main(int argc, char** argv)
{
    /*1,1,1,1,1,1,1,1,3,5,5,7,9,10,10,12,15,16,17,18,19,100,1000*/
    int a[] = {5, 15, 5, 7, 9, 17,100, 3, 12, 10, 19, 18, 16, 10, 1000,1,1,1,1,1,1,1,1};
    int r = selectk(a, 0, sizeof(a) /sizeof(int) - 1, 5);
    cout<<(r == -1 ? r : a[r])<<endl;
    return 0;
}

    
     
