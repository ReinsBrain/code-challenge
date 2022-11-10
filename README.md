# code-challenge

```js
console.info('1 - Non-Constructible Change');

function getMinChange ( coins ) {
	let sorted = coins.sort((a,b)=>{ return a-b});
	let sum = 1;
	for ( let i = 0; i < sorted.length; i++ ) {
		if ( sum < sorted[i] ) {
			return sum;
		}
		sum += sorted[i];
	}
	return sum;
}

console.assert( getMinChange( [5, 7, 1, 1, 2, 3, 22]) == 20, 'it should equal 20' );
console.assert( getMinChange( [1, 1, 1, 1, 1]) == 6, 'it should equal 6' );
console.assert( getMinChange( [1, 5, 1, 1, 1, 10, 15, 20, 100] ) == 55, 'it should equal 55' );
console.info("Complexity: O(log n) [the sort] + O(m) [the loop on the array] ~= O(log n)")

console.info('2 - Sorted Squared Array');
function squareArray( sortedArray ) {
	let negNums = [];
	let squaredArray = [];
	while ( sortedArray.length > 0 || negNums.length > 0 ) {
		if ( sortedArray.length > 0 && sortedArray[0] < 0 ) {
			negNums.push( sortedArray.shift() * -1 );
			continue;
		}
		if ( negNums.length > 0 && ( sortedArray.length == 0 || negNums[negNums.length-1] <= sortedArray[0] ) ) {
		squaredArray.push( Math.pow( negNums.pop(), 2 ) );
		} else {
			if ( sortedArray.length > 0 ) {
				squaredArray.push( Math.pow( sortedArray.shift(), 2 ) );
			}
		}
	}
	return squaredArray;
}

console.assert( JSON.stringify( squareArray( [1, 2, 3, 5, 6, 8, 9] ) ) == JSON.stringify( [1, 4, 9, 25, 36, 64, 81] ), 'it should equal [1, 4, 9, 25, 36, 64, 81]' );
console.assert( JSON.stringify( squareArray( [-2, -1] ) ) == JSON.stringify( [1, 4] ), 'it should equal [1, 4]' );
console.assert( JSON.stringify( squareArray( [-10, -5, 0, 5, 10] ) ) == JSON.stringify( [0, 25, 25, 100, 100] ), 'it should equal [0, 25, 25, 100, 100]');
console.info('Complexity: O(n)');
```
