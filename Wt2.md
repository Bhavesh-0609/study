# Node
1. Create a one buffer to allocate the appropriate size. Write the message in the buffer “The scientist discovers a new type of material or energy, and the engineer discovers a new use for it”. print it in the console in human readable form.
```
// Method 1
// let buf = new Buffer(40);
// buf = Buffer.from('The scientist discovers a new type of material or energy, and the engineer discovers a new use for it',"utf8");
// console.log(buf.toString());

// Method 2
let buf = new Buffer("hello world","utf8");
console.log(buf.toString());
```
2. Consider the file demo.txt and write and read the content using Stream and buffer.
demo.txt
“The scientist discovers a new type of material or energy, and the engineer discovers a new use for it”.
