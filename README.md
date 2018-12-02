**deepr** is a set of functions for modifying nested objects.

 **merge()**
```javascript
// Set the value of the array
const arr = deepr.merge([1], [2]);
console.log(arr);	// [2]

// **Set** the value of missing key
const obj = deepr.merge({}, {
	arr: [2]
});
console.log(obj);	// { arr: [2] }

// **Push** a vlue to an array
const arr = deepr.merge([1], ['&push', 2]);
console.log(arr); // [1, 2];

// **Concat** a value to an array
const arr = deepr.merge([1], ['&concat', [2, 3]]);
// [1, 2, 3]

// **Pop** a value from an array
const arr = deepr.merge([1,2,3], ['&pop']);
// [1, 2];

// **Shift** a value from an array
const arr = deepr.merge([1,2,3], ['&shift']);
// [2, 3]

// **Unshift** a vaule to the arry
const arr = deepr.merge([1,2,3], ['&unshift', 0]);
// [0,1,2,3]

// Deep merge an object
const obj = deepr.merge({
	nested: {key: 'val'}
}, {
	nested: {key: 'deep val'}
});
// { nested: { key: 'deep val' } }

// Empty an object
const obj = deepr.merge({
	object: { key: 'val' },
}, {
	object: '&={}'
});
// { object: {} };

// Set object to empty array
const obj = deepr.merge({
	object: { key: 'val' },
}, {
	object: '&=[]'
});

// Set primative values
const obj = deepr.merge({
	truth: true,
	integer: 1,
	string: 'prev',
	type: 'string',
}, {
	truth: false,
	integer: 2,
	string: 'next',
	add: 'key',
	type: 1
});
// { truth: false, integer: 2, string: 'next', add: 'key', type: 1 };

// Add one to a value
const obj = deepr.merge({}, { counts: { up: '&+=1'} });
// { counts: { up: 1 } }

// Subtrack one from a value
const obj = deepr.merge({up: 2}, {up: '&-=1'})
// {up: 1}

// Multiply the value by x
const obj = deepr.merge({ up: 5 }, { up: '&*=5' });
// {up: 25}

// Divide the value by x
const obj = deepr.merge({ up: 25 }, { up: '&/=5' });
// {up: 5}

// **isDestructive** returns true if a method is destructive
const res = deepr.isDestructive('&delete'); // true
const res = deepr.isDestructive('&={}'); // true
const res = deepr.isDestructive('&=[]'); // true
```
