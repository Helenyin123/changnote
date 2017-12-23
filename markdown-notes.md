# Title

# Heading1

## Heading2

### Heading3

#### Heading4

##### Heading5

###### Heading6

# List

* Unorder list
  * sub list
    * sub list
* like this
* txt

1. Order List
   1. sub list
   2. sub list
2. like this
3. txt

# Horizontal Rule

---

First Row

---

Second Row

---

Third Row

---

# Link & Photo & Email

[Google](http://www.google.com)

![](/assets/Screen Shot 2016-08-18 at 3.04.37 PM.png) My Awesome Book

[yin100@usc.edu](yin100@usc.edu)

# Block Quote

> Having anybody know this function at all. -- by Somebody something

# Bold & Italic

**Bold**

_Italic_

# Code Snippet

### Single Line

`int a = 0;`

### Snippet

```java
    public int calculate(String s) {
        if (s == null || s.length() == 0) return 0;
        Stack<Character> stack = new Stack<Character>();
        for (int i = s.length()- 1; i >= 0; i --) stack.push(s.charAt(i));
        return cal(stack);
    }
    private int cal(Stack<Character> stack) {
        int result = 0, number = 0, sign = 1;
        while(!stack.isEmpty()) {
            char ch = stack.pop();
            if (ch >= '0' && ch <= '9') {
                number = 10 * number + ch - '0';
            } else if (ch == '+') {
                result += sign * number;
                number = 0;
                sign = 1;
            } else if (ch == '-') {
                result += sign * number;
                number = 0;
                sign = -1;
            } else if (ch == '(') {
                number = cal(stack);
            } else if (ch == ')') {
                result += sign * number;
                return result;
            }
        }
        if (number != 0) result += sign * number;
        return result;
    }
```

# Table

| Tables | Are | Cool |
| --- | :---: | ---: |
| col 3 is | right-aligned | $1600 |
| col 2 is | centered | $12 |
| zebra stripes | are neat | $1 |

| dog | bird | cat |
| --- | --- | --- |
| foo | foo | foo |
| bar | bar | bar |
| baz | baz | baz |

# Footnote

This is a txt footnote[^1]

# [Special Characters](http://rabbit.eng.miami.edu/info/htmlchars.html)

&ltem&gt; &lt;&gt;

&

[^1]: This is footnote 1 in the text

