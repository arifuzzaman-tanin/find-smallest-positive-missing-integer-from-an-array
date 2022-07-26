```html
Write a function:

class Solution { public int solution(int[] A); }

that, given an array A of N integers, returns the smallest positive integer (greater than 0) that does not occur in A.

For example, given A = [1, 3, 6, 4, 1, 2], the function should return 5.

Given A = [1, 2, 3], the function should return 4.

Given A = [−1, −3], the function should return 1.

Write an efficient algorithm for the following assumptions:

N is an integer within the range [1..100,000];
each element of array A is an integer within the range [−1,000,000..1,000,000].
```

```javascript
function solution(A) {
    let sortedArray = A.sort();
    let uniqueElements = [];
    let mapElements = {};
    for (let element of sortedArray) {
        if (!mapElements[element]) {
            mapElements[element] = true;
            uniqueElements.push(element);
        }
    }

    let maxElement = sortedArray[sortedArray.length - 1];
    let minElement = sortedArray[0];

    if (minElement < 0 && maxElement < 0) {
        return 1;
    }

    for (let i = minElement; i <= maxElement; i++) {
        if (!mapElements[i]) {
            return i;
        }
    }

    return ++maxElement;
}


console.log(solution([1, 3, 6, 4, 1, 2]));
```

Output

```html
5
```