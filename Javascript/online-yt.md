3 Ways to convert String to Numbers
.
+, Number and parseInt.  these three Number() and Unary Plus(+) works exactly same.

Below are the major differences between Number constructor function and parseInt.
1. Number(x) does type coercion to number, while parseInt(x) does parsing.

2.Number works well with Scientific Numbers
Number("83e4"); // 830000
Number("2e2"); // 200

parseInt('4e3'); // 4

3. Empty, Nullish value handling is different.
Number(""); // 0
Number(false); // 0
Number(null); // 0
Number([]); // 0

Number(true); // 1

parseInt(""); // NaN
parseInt(null); // NaN
parseInt(false); // NaN
parseInt([]); // NaN

parseInt(true); // NaN

parseInt(undefined); // NaN
parseInt({}); // NaN

Number({}); // NaN

4. Number() can’t differentiate different Number System, but parseInt can with radix argument.
parseInt(10,8)// Octal conversion - output 8
parseInt(101,2)// Binary conversion - output 5

Similarity:
They both also ignore whitespace:
const foo = "    6  ";
console.log(parseInt(foo)); // 6
console.log(Number(foo)); // 6
