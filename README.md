## Welcome to Alicorn's blog

```c++
#include <iostream>
#include <deque>
#include <vector>
using namespace std;
/*
 * monotonic queue is a queue in which the element sequence is monotonic
 * for example
 */
int main()
{
    int n, k;
    cin >> n >> k;
    vector<int> vec(n);
    for (int i = 0; i < n; ++i) {
        cin >> vec[i];
    }
    deque<int> dq; // monotonic queue is not traditional queue, we must use double end queue to simulate
    for (int i = 0; i < n; ++i) {
        /*
         *
         */
        while (!dq.empty() && vec[dq.back()] >= vec[i]) {
            dq.pop_back();
        }
        dq.push_back(i); // store the tail element, in dq means dq.back()
        while (!dq.empty() && i - k >= dq.front()) {
            dq.pop_front();
        }
        if (i >= k - 1) {
            cout << vec[dq.front()] << " ";
        }
    }
    cout << endl;
    dq.clear();
    for (int i = 0; i < n; ++i) {
        while (!dq.empty() && vec[dq.back()] <= vec[i]) {
            dq.pop_back();
        }
        dq.push_back(i);
        while (!dq.empty() && i - k >= dq.front()) {
            dq.pop_front();
        }
        if (i >= k - 1) {
            cout << vec[dq.front()] << " ";
        }
    }
    return 0;
}
```
