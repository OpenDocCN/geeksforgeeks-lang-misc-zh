# 使用 Perl 的猜数字游戏

> 原文:[https://www . geeksforgeeks . org/number-guess-game-use-perl/](https://www.geeksforgeeks.org/number-guessing-game-using-perl/)

数字猜谜游戏就是在给定的概率下，猜测计算机随机选择的数字。

**要使用的功能:**

1.  **rand n :** 这个函数用来生成一个 0 到 n 之间的随机数，并且这个函数总是返回浮点数。所以它的结果被显式转换为整数值。
2.  **Chomp() :** 此功能用于从用户输入中删除换行符。

**说明:**
在程序中，while 循环运行，直到用户猜测的次数等于生成的次数或者尝试次数小于最大机会次数。如果尝试次数变得大于机会次数，则游戏停止，用户输掉游戏。如果用户在给定的概率中猜出正确的数字，那么他或她将获胜。在用户进行每一次猜测后，程序会通知用户猜测的数字是否小于、大于实际生成的数字。
在这段代码中，最初， **rand 函数**选择一个随机数作为 x，函数(rand k)找到一个 0 到 k 之间的随机数，由于这个随机数是一个浮点数，所以**用“int”**将其显式转换为整数。x 存储整数。用户被给予特定数量的机会来猜测该数量，如果该机会超过用户猜测的，则用户将会失败。

下面是实现:

```perl
# Number Guessing Game implementation 
# using Perl Programming 

print "Number guessing game\n";

# rand function to generate the
# random number b/w 0 to 10
# which is converted to integer
# and store to the variable "x"
$x = int rand 10;

# variable to count the correct
# number of chances
$correct = 0;

# number of chances to be given
# to the user to guess number
# the number or it is the of
# inputs given by user into 
# input box here number of 
# chances are 4
$chances = 4;
$n = 0;

print "Guess a number (between 0 and 10): \n";

# while loop containing variable n
# which is used as counter value 
# variable chance
while($n < $chances)
{

    # Enter a number between 0 to 10
    # Extract the number from input
    # and remove newline character
    chomp($userinput = <STDIN>);

    # To check whether user provide
    # any input or not
    if($userinput != "blank")
    {

        # Compare the user entered number 
        # with the number to be guessed 
        if($x == $userinput)
        {

            # if number entered by user 
            # is same as the generated 
            # number by rand function then 
            # break from loop using loop
            # control statement "last"
            $correct = 1; 
            last;
        }

        # Check if the user entered 
        # number is smaller than 
        # the generated number
        elsif($x > $userinput)
        {
            print "Your guess was too low,"; 
            print " guess a higher number than ${userinput}\n";
        }

        # The user entered number is 
        # greater than the generated
        # number
        else
        {
            print "Your guess was too high,";
            print " guess a lower number than ${userinput}\n";
        }

        # Number of chances given 
        # to user increases by one
        $n++;

}
    else
    {
        $chances--;
    }
}

    # Check whether the user 
    # guessed the correct number
    if($correct == 1)
    {
            print "You Guessed Correct!"; 
            print " The number was $x";
    }
    else
    {
            print "It was actually ${x}.";
    }

```

**输入:**

```perl
5
6
8
9

```

**输出:**

```perl
Number guessing game
Guess a number (between 0 and 10): 
Your guess was too low, guess a higher number than 5
Your guess was too low, guess a higher number than 6
Your guess was too low, guess a higher number than 8
You Guessed Correct! The number was 9

```

**注意:**在上面的程序中，用户可以修改**和**函数的值来增加游戏中的数字范围，用户也可以通过增加机会变量的值来增加机会的数量。