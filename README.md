<div align="center">

## Flags, the Binary system and Logic operators\.


</div>

### Description

This article teaches how and why to use "flags", and goes through the Binary System and Logic Operators to explain this. Please give feedback and/or vote if you think this could be of benefit to alot of programmers. I got the idea for this article while making an ActiveX DLL for a card game, so the I promise article is applicable to many real programming problems and I do practice what I preach. - Simon Price http://www.VBgames.co.uk
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Simon Price](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/simon-price.md)
**Level**          |Intermediate
**User Rating**    |4.9 (93 globes from 19 users)
**Compatibility**  |VB 3\.0, VB 4\.0 \(16\-bit\), VB 4\.0 \(32\-bit\), VB 5\.0, VB 6\.0, VB Script, ASP \(Active Server Pages\) , VBA MS Access, VBA MS Excel
**Category**       |[Coding Standards](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/coding-standards__1-43.md)
**World**          |[Visual Basic](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/visual-basic.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/simon-price-flags-the-binary-system-and-logic-operators__1-25738/archive/master.zip)





### Source Code

<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=windows-1252">
<meta name="GENERATOR" content="Microsoft FrontPage 4.0">
<meta name="ProgId" content="FrontPage.Editor.Document">
<title>Flags</title>
</head>
<body>
<h1 align="left">Flags, the Binary system and Logic operators.</h1>
<h2 align="left">Introduction</h2>
<p align="left">"Flags" are often used in programming when something
can be either "on" or "off", in other words, a Boolean
variable. This tutorial describes how and why to use flags. It uses Visual Basic
for example code, but this technique can be applied to all languages.</p>
<h2 align="left">An example situation</h2>
<p align="left">Here is an imaginary form about the features of a futuristic
car.</p>
<form method="POST" action="--WEBBOT-SELF--" onSubmit>
 <table border="1" width="100%">
 <tr>
 <td width="100%">
 <p align="left">Please choose an option to show which feature you would
 like on your new car:</p>
 <p align="left"><input type="radio" value="V9" name="R1"> [1] Jet boost</p>
 <p align="left"><input type="radio" value="V10" name="R1"> [2]
 Invulnerability shield</p>
 <p align="left"><input type="radio" value="V11" name="R1"> [3]
 Anti-Gravity generator</p>
 <p align="left"><input type="radio" value="V12" name="R1"> [4] Missile
 proof glass</p>
 <p align="left"><input type="radio" value="V13" name="R1"> [5] Instant
 stop brakes</p>
 <p align="left"><input type="radio" value="V14" name="R1"> [6] Super
 grip tires</p>
 <p align="left"><input type="radio" value="V15" name="R1"> [7] 10000
 horsepower engine</p>
 <p align="left"><input type="radio" value="V16" name="R1"> [8] Time warp
 drive</td>
 </tr>
 </table>
</form>
<p align="left">We can think of each feature as a Boolean value, it is either on
the car, or not on the car.</p>
<p align="left">Lets imagine you want to store the results to your questionnaire
in 1 byte of data. This is simple, you just label the features from [1] through
to [8] and save that number. Job done? Not yet! Unfortunately, this method is
not very clever.</p>
<h2 align="left">The problem</h2>
<p align="left">One of your customers, Mr. Richguy, who has a lot of money to
spend on his new car decides he wants TWO features on his car! Oh no, better
redesign that form with checkboxes instead of radio buttons. You slave away
designing your new form so that it looks like this.</p>
<form method="POST" action="--WEBBOT-SELF--" onSubmit>
 <table border="1" width="100%">
 <tr>
 <td width="100%">
 <p align="left">Please choose any number of option/s to show which
 feature/s you would like on your new car:</p>
 <p align="left"><input type="checkbox" name="C1" value="ON"> [1] Jet
 boost</p>
 <p align="left"><input type="checkbox" name="C2" value="ON"> [2]
 Invulnerability shield</p>
 <p align="left"><input type="checkbox" name="C3" value="ON"> [3]
 Anti-Gravity generator</p>
 <p align="left"><input type="checkbox" name="C4" value="ON"> [4] Missile
 proof glass</p>
 <p align="left"><input type="checkbox" name="C5" value="ON"> [5] Instant
 stop brakes</p>
 <p align="left"><input type="checkbox" name="C6" value="ON"> [6] Super
 grip tires</p>
 <p align="left"><input type="checkbox" name="C7" value="ON"> [7] 10000
 horsepower engine</p>
 <p align="left"><input type="checkbox" name="C8" value="ON"> [8] Time
 warp drive</td>
 </tr>
 </table>
</form>
<p align="left">Great! Now we can choose to have 1 feature, several features, or
no features at all!</p>
<h2 align="left">The quick-fix solution</h2>
<p align="left">How do we save this information? We could use an array of 8
Boolean variables and save each one separately. That would work, but assuming
your code uses a whole byte to store a Boolean variable (as in C/C++/Delphi
etc., and VB I have heard uses 2 bytes!), that would take 8 bytes to store your
results rather than just the 1 we had before. What's that you say? You have
512MB SD RAM and 100GB hard drive? So you don't care about this memory wastage?
Then I shall show you another problem with this method.</p>
<p align="left">Lets imagine we want to pass this information into a function.
Maybe the function would calculate the cost of the car, given it's features. You
could pass the Boolean variable for each feature into the function. It might
look a bit like this (using VB code).</p>
<table border="1" width="100%">
 <tr>
 <td width="100%">Function CostOfCar(Feature1 As Boolean, Feature2 As
 Boolean, Feature3 As Boolean, Feature4 As Boolean, Feature5 As Boolean,
 Feature6 As Boolean, Feature7 As Boolean, Feature8 As Boolean) As Integer<br>
 Dim x As Integer<br>
    ' do something with the feature list to calculate the cost of
 the car<br>
    CostOfCar = x<br>
 End Function</td>
 </tr>
</table>
<p>Doesn't look like a very neat function does it? Rather ugly in fact.</p>
<h2>The smart solution</h2>
<p>This is how it should be done! Using a whole byte to store a Boolean is a
waste. We really only need 1 bit, a 0 representing False (or off) and a 1
representing True (or on). Many of you will know how the Binary system and logic
operations work, but I will explain it here because it is important you
understand these first.</p>
<h3>The Binary system</h3>
<p>A bit can either be a 0 or a 1, on or off, true or false. A byte consists of
8 bits. Each bit in the byte represents a different power of 2. In this way, a
byte can store any number from 0 to 255. This table shows some examples. Note
that the "^" sign stands for "to the power of".</p>
<table border="1" width="100%">
 <tr>
 <td width="11%">Bit1</td>
 <td width="11%">Bit2</td>
 <td width="11%">Bit3</td>
 <td width="11%">Bit4</td>
 <td width="11%">Bit5</td>
 <td width="11%">Bit6</td>
 <td width="11%">Bit7</td>
 <td width="11%">Bit8</td>
 <td width="12%">Byte</td>
 </tr>
 <tr>
 <td width="11%">2^0=1</td>
 <td width="11%">2^1=2</td>
 <td width="11%">2^2=4</td>
 <td width="11%">2^3=8</td>
 <td width="11%">2^4=16</td>
 <td width="11%">2^5=32</td>
 <td width="11%">2^6=64</td>
 <td width="11%">2^7=128</td>
 <td width="12%">Total</td>
 </tr>
 <tr>
 <td width="11%">0</td>
 <td width="11%">0</td>
 <td width="11%">0</td>
 <td width="11%">0</td>
 <td width="11%">0</td>
 <td width="11%">0</td>
 <td width="11%">0</td>
 <td width="11%">0</td>
 <td width="12%">0</td>
 </tr>
 <tr>
 <td width="11%">1</td>
 <td width="11%">0</td>
 <td width="11%">0</td>
 <td width="11%">0</td>
 <td width="11%">0</td>
 <td width="11%">0</td>
 <td width="11%">0</td>
 <td width="11%">0</td>
 <td width="12%">1</td>
 </tr>
 <tr>
 <td width="11%">1</td>
 <td width="11%">0</td>
 <td width="11%">1</td>
 <td width="11%">0</td>
 <td width="11%">1</td>
 <td width="11%">0</td>
 <td width="11%">0</td>
 <td width="11%">0</td>
 <td width="12%">21</td>
 </tr>
 <tr>
 <td width="11%">0</td>
 <td width="11%">1</td>
 <td width="11%">1</td>
 <td width="11%">1</td>
 <td width="11%">1</td>
 <td width="11%">0</td>
 <td width="11%">0</td>
 <td width="11%">0</td>
 <td width="12%">30</td>
 </tr>
 <tr>
 <td width="11%">1</td>
 <td width="11%">0</td>
 <td width="11%">0</td>
 <td width="11%">0</td>
 <td width="11%">0</td>
 <td width="11%">0</td>
 <td width="11%">0</td>
 <td width="11%">1</td>
 <td width="12%">129</td>
 </tr>
 <tr>
 <td width="11%">0</td>
 <td width="11%">1</td>
 <td width="11%">1</td>
 <td width="11%">0</td>
 <td width="11%">0</td>
 <td width="11%">0</td>
 <td width="11%">0</td>
 <td width="11%">1</td>
 <td width="12%">134</td>
 </tr>
 <tr>
 <td width="11%">0</td>
 <td width="11%">0</td>
 <td width="11%">0</td>
 <td width="11%">0</td>
 <td width="11%">0</td>
 <td width="11%">0</td>
 <td width="11%">1</td>
 <td width="11%">1</td>
 <td width="12%">194</td>
 </tr>
 <tr>
 <td width="11%">1</td>
 <td width="11%">0</td>
 <td width="11%">0</td>
 <td width="11%">1</td>
 <td width="11%">1</td>
 <td width="11%">1</td>
 <td width="11%">1</td>
 <td width="11%">1</td>
 <td width="12%">249</td>
 </tr>
 <tr>
 <td width="11%">1</td>
 <td width="11%">1</td>
 <td width="11%">1</td>
 <td width="11%">1</td>
 <td width="11%">1</td>
 <td width="11%">1</td>
 <td width="11%">1</td>
 <td width="11%">1</td>
 <td width="12%">255</td>
 </tr>
</table>
<h3>Logical Operations</h3>
<p>The logical operators I will demonstrate here (there are more) are And &
Or. All logic operators work on a bit level.</p>
<p>The And operator takes two bits (we will call Bit1 and Bit2), and returns a 1
only if Bit1 AND Bit2 are 1. This table shows all the possible outcomes of the
And operator.</p>
<table border="1" width="100%">
 <tr>
 <td width="33%">Bit1</td>
 <td width="33%">Bit2</td>
 <td width="34%">Bit1 And Bit2</td>
 </tr>
 <tr>
 <td width="33%">0</td>
 <td width="33%">0</td>
 <td width="34%">0</td>
 </tr>
 <tr>
 <td width="33%">0</td>
 <td width="33%">1</td>
 <td width="34%">0</td>
 </tr>
 <tr>
 <td width="33%">1</td>
 <td width="33%">0</td>
 <td width="34%">0</td>
 </tr>
 <tr>
 <td width="33%">1</td>
 <td width="33%">1</td>
 <td width="34%">1</td>
 </tr>
</table>
<p>The Or operator takes two bits (again, Bit1 and Bit2), and returns a 1 if
either Bit1 OR Bit2 are 1. This table shows all the possible outcomes of the Or
operator.</p>
<table border="1" width="100%">
 <tr>
 <td width="33%">Bit1</td>
 <td width="33%">Bit2</td>
 <td width="34%">Bit1 Or Bit2</td>
 </tr>
 <tr>
 <td width="33%">0</td>
 <td width="33%">0</td>
 <td width="34%">0</td>
 </tr>
 <tr>
 <td width="33%">0</td>
 <td width="33%">1</td>
 <td width="34%">1</td>
 </tr>
 <tr>
 <td width="33%">1</td>
 <td width="33%">0</td>
 <td width="34%">1</td>
 </tr>
 <tr>
 <td width="33%">1</td>
 <td width="33%">1</td>
 <td width="34%">1</td>
 </tr>
</table>
<p>As I said before, logical operators work on bits. So how comes this code is
valid?</p>
<table border="1" width="100%">
 <tr>
 <td width="100%">' declare some byte variables
 <p>Dim Byte1 As Byte</p>
 <p>Dim Byte2 As Byte</p>
 <p>Dim ByteResult As Byte</p>
 <p>' give the bytes some values</p>
 <p>Byte1 = 51</p>
 <p>Byte2 = 219</p>
 <p>' use the or operator</p>
 <p>ByteResult = ( Byte1 Or Byte2)</p>
 <p>' show the result in the debug window</p>
 <p>Debug.Print ByteResult</p>
 <p>' use the and operator</p>
 <p>ByteResult = ( Byte1 And Byte2)</p>
 <p>' show the result in the debug window</p>
 <p>Debug.Print ByteResult</td>
 </tr>
</table>
<p>This code works because the Or & And operators are working on each bit of
each byte. Here is how the and Or operation worked.</p>
<table border="1" width="100%">
 <tr>
 <td width="11%">Bit</td>
 <td width="11%">Bit1</td>
 <td width="11%">Bit2</td>
 <td width="11%">Bit3</td>
 <td width="11%">Bit4</td>
 <td width="11%">Bit5</td>
 <td width="11%">Bit6</td>
 <td width="11%">Bit7</td>
 <td width="12%">Bit8</td>
 <td width="12%">Total</td>
 </tr>
 <tr>
 <td width="11%">Value</td>
 <td width="11%">[1]</td>
 <td width="11%">[2]</td>
 <td width="11%">[4]</td>
 <td width="11%">[8]</td>
 <td width="11%">[16]</td>
 <td width="11%">[32]</td>
 <td width="11%">[64]</td>
 <td width="12%">[128]</td>
 <td width="12%">[255]</td>
 </tr>
 <tr>
 <td width="11%">Byte1</td>
 <td width="11%">1</td>
 <td width="11%">1</td>
 <td width="11%">0</td>
 <td width="11%">0</td>
 <td width="11%">1</td>
 <td width="11%">1</td>
 <td width="11%">0</td>
 <td width="12%">0</td>
 <td width="12%">51</td>
 </tr>
 <tr>
 <td width="11%">Byte2</td>
 <td width="11%">1</td>
 <td width="11%">1</td>
 <td width="11%">0</td>
 <td width="11%">1</td>
 <td width="11%">1</td>
 <td width="11%">0</td>
 <td width="11%">1</td>
 <td width="12%">1</td>
 <td width="12%">219</td>
 </tr>
 <tr>
 <td width="11%">Byte1 Or Byte2</td>
 <td width="11%">1</td>
 <td width="11%">1</td>
 <td width="11%">0</td>
 <td width="11%">1</td>
 <td width="11%">1</td>
 <td width="11%">1</td>
 <td width="11%">1</td>
 <td width="12%">1</td>
 <td width="12%">251</td>
 </tr>
</table>
<p>And this is how the And operation worked.</p>
<table border="1" width="100%">
 <tr>
 <td width="11%">Bit</td>
 <td width="11%">Bit1</td>
 <td width="11%">Bit2</td>
 <td width="11%">Bit3</td>
 <td width="11%">Bit4</td>
 <td width="11%">Bit5</td>
 <td width="11%">Bit6</td>
 <td width="11%">Bit7</td>
 <td width="12%">Bit8</td>
 <td width="12%">Total</td>
 </tr>
 <tr>
 <td width="11%">Value</td>
 <td width="11%">[1]</td>
 <td width="11%">[2]</td>
 <td width="11%">[4]</td>
 <td width="11%">[8]</td>
 <td width="11%">[16]</td>
 <td width="11%">[32]</td>
 <td width="11%">[64]</td>
 <td width="12%">[128]</td>
 <td width="12%">[255]</td>
 </tr>
 <tr>
 <td width="11%">Byte1</td>
 <td width="11%">1</td>
 <td width="11%">1</td>
 <td width="11%">0</td>
 <td width="11%">0</td>
 <td width="11%">1</td>
 <td width="11%">1</td>
 <td width="11%">0</td>
 <td width="12%">0</td>
 <td width="12%">51</td>
 </tr>
 <tr>
 <td width="11%">Byte2</td>
 <td width="11%">1</td>
 <td width="11%">1</td>
 <td width="11%">0</td>
 <td width="11%">1</td>
 <td width="11%">1</td>
 <td width="11%">0</td>
 <td width="11%">1</td>
 <td width="12%">1</td>
 <td width="12%">219</td>
 </tr>
 <tr>
 <td width="11%">Byte1 Or Byte2</td>
 <td width="11%">1</td>
 <td width="11%">1</td>
 <td width="11%">0</td>
 <td width="11%">0</td>
 <td width="11%">1</td>
 <td width="11%">0</td>
 <td width="11%">0</td>
 <td width="12%">0</td>
 <td width="12%">19</td>
 </tr>
</table>
<p>If you have VB and ran this code, you should find the results 251 and 19 in
your debug window.</p>
<h3>Applying your new knowledge!</h3>
<p>Getting a bit bored of all these tables of 0's and 1's? Don't worry, you
didn't read all that for nothing! Lets go back to the problem of storing car
features. Instead of assigning each feature a value from [1] to [8], we instead
use [2^0] to [2^7], like this.</p>
<form method="POST" action="--WEBBOT-SELF--" onSubmit>
 <table border="1" width="100%">
 <tr>
 <td width="100%">
 <p align="left">Please choose any option/s to show which feature/s you
 would like on your new car:</p>
 <p align="left"><input type="checkbox" name="C1" value="ON"> [2^0=1] Jet
 boost</p>
 <p align="left"><input type="checkbox" name="C2" value="ON"> [2^1=2]
 Invulnerability shield</p>
 <p align="left"><input type="checkbox" name="C3" value="ON"> [2^2=4]
 Anti-Gravity generator</p>
 <p align="left"><input type="checkbox" name="C4" value="ON"> [2^3=8]
 Missile proof glass</p>
 <p align="left"><input type="checkbox" name="C5" value="ON"> [2^4=16]
 Instant stop brakes</p>
 <p align="left"><input type="checkbox" name="C6" value="ON"> [2^5=32]
 Super grip tires</p>
 <p align="left"><input type="checkbox" name="C7" value="ON"> [2^6=64]
 10000 horsepower engine</p>
 <p align="left"><input type="checkbox" name="C8" value="ON"> [2^7=128]
 Time warp drive</td>
 </tr>
 </table>
</form>
<p>Now, we use an enumeration to store the possible features. In Visual Basic,
it would look something like this.</p>
<table border="1" width="100%">
 <tr>
 <td width="100%">Enum CAR_FEATURE
 <p>   CF_JETBOOST = 1</p>
 <p>   CF_SHIELD = 2</p>
 <p>   CF_ANTIGRAVITY = 4</p>
 <p>   CF_GLASS = 8</p>
 <p>   CF_BRAKES = 16</p>
 <p>   CF_TIRES = 32</p>
 <p>   CF_ENGINE = 64</p>
 <p>   CF_TIMEWARP = 128</p>
 <p>End Enum</td>
 </tr>
</table>
<p>Now we can store 8 features into just 1 byte! To do this, we just add all the
features up, using the + operator. For example, Mr. Richguy comes back to your
online car showroom now you have improved it to allow for multiple features, and
decides to buy a new car with jet boost, a shield, super grip tires and a time
warp.
<p> 
<table border="1" width="100%">
 <tr>
 <td width="100%">
 <p>Dim Features As Byte
 <p>Features = CF_JETBOOST + CF_SHIELD + CF_TIRES + CD_TIMEWARP
 <p>Debug.Print Features</td>
 </tr>
</table>
<p>This code stores all the features Mr. Richguy requested in a single byte, of
value 163, which could be saved in a file, or sent to function to add up the
cost, or anything else you'd like to do with it.</p>
<p>You new function to calculate the cost would look much simpler, something
like this.</p>
<table border="1" width="100%">
 <tr>
 <td width="100%">Function CostOfCar(Features As Byte) As Integer<br>
 Dim x As Integer<br>
    ' do something with the features byte to calculate the cost
 of the car<br>
    CostOfCar = x<br>
 End Function</td>
 </tr>
</table>
<p>Note how each feature is actually represented by one of the bits in your
byte.</p>
<p>However, there comes a time when you want to reverse the operation and get
the features back out of the byte variable, such as when you load a file, or the
function parses the features etc. How is this done? I didn't mention logic
operators for nothing!</p>
<p>Imagine our function wants to test if there are super grip tires to be put
onto the new car. What we would need to do is test whether the CF_TIRES was in
the byte. The number 32 (=2^5) is represented by Bit6 of your byte. To check is
Bit6 is present (=1), you can use the And operator. For example:</p>
<table border="1" width="100%">
 <tr>
 <td width="100%">' see whether the car has super grip tires
 <p>If (Features And CF_TIRES = CF_TIRES) Then</p>
 <p>   ' do something, like add some cost according to the size
 of the wheels etc.</p>
 <p>End If</td>
 </tr>
</table>
<p>So how did this work? Well, what we did was to see whether And'ing the
features with tires caused the result of tires. To see why this works, look at
the table.</p>
<table border="1" width="100%">
 <tr>
 <td width="11%"> </td>
 <td width="11%">Bit1</td>
 <td width="11%">Bit2</td>
 <td width="11%">Bit3</td>
 <td width="11%">Bit4</td>
 <td width="11%">Bit5</td>
 <td width="11%">Bit6</td>
 <td width="11%">Bit7</td>
 <td width="12%">Bit8</td>
 <td width="12%">Total</td>
 </tr>
 <tr>
 <td width="11%">Features</td>
 <td width="11%">1</td>
 <td width="11%">1</td>
 <td width="11%">0</td>
 <td width="11%">0</td>
 <td width="11%">0</td>
 <td width="11%">1</td>
 <td width="11%">0</td>
 <td width="12%">1</td>
 <td width="12%">163</td>
 </tr>
 <tr>
 <td width="11%">CF_TIRES</td>
 <td width="11%">0</td>
 <td width="11%">0</td>
 <td width="11%">0</td>
 <td width="11%">0</td>
 <td width="11%">0</td>
 <td width="11%">1</td>
 <td width="11%">0</td>
 <td width="12%">0</td>
 <td width="12%">32</td>
 </tr>
 <tr>
 <td width="11%">Features And CF_TIRES</td>
 <td width="11%">0</td>
 <td width="11%">0</td>
 <td width="11%">0</td>
 <td width="11%">0</td>
 <td width="11%">0</td>
 <td width="11%">1</td>
 <td width="11%">0</td>
 <td width="12%">0</td>
 <td width="12%">32</td>
 </tr>
</table>
<p>In a similar way, the Or operator could have been used to find whether tires
were in the features byte.</p>
<table border="1" width="100%">
 <tr>
 <td width="100%">' see whether the car has super grip tires
 <p>If (Features Or CF_TIRES) = Features Then</p>
 <p>   ' do something, like add some cost according to the size
 of the wheels etc.</p>
 <p>End If</td>
 </tr>
</table>
<p>So how did it work again? Well, what we did was to see whether Or'ing the
features with tires caused the result of features. To see why this also works,
look at the table.</p>
<table border="1" width="100%">
 <tr>
 <td width="11%"> </td>
 <td width="11%">Bit1</td>
 <td width="11%">Bit2</td>
 <td width="11%">Bit3</td>
 <td width="11%">Bit4</td>
 <td width="11%">Bit5</td>
 <td width="11%">Bit6</td>
 <td width="11%">Bit7</td>
 <td width="12%">Bit8</td>
 <td width="12%">Total</td>
 </tr>
 <tr>
 <td width="11%">Features</td>
 <td width="11%">1</td>
 <td width="11%">1</td>
 <td width="11%">0</td>
 <td width="11%">0</td>
 <td width="11%">0</td>
 <td width="11%">1</td>
 <td width="11%">0</td>
 <td width="12%">1</td>
 <td width="12%">163</td>
 </tr>
 <tr>
 <td width="11%">CF_TIRES</td>
 <td width="11%">0</td>
 <td width="11%">0</td>
 <td width="11%">0</td>
 <td width="11%">0</td>
 <td width="11%">0</td>
 <td width="11%">1</td>
 <td width="11%">0</td>
 <td width="12%">0</td>
 <td width="12%">32</td>
 </tr>
 <tr>
 <td width="11%">Features And CF_TIRES</td>
 <td width="11%">1</td>
 <td width="11%">1</td>
 <td width="11%">0</td>
 <td width="11%">0</td>
 <td width="11%">0</td>
 <td width="11%">1</td>
 <td width="11%">0</td>
 <td width="12%">1</td>
 <td width="12%">163</td>
 </tr>
</table>
<p>It doesn't really matter whether you use the And operator or the Or operator
to do this, but this process is often called "Masking" bits.</p>
<h2>Summary</h2>
<p>You have learnt about storing multiple Boolean variables ("flags")
in a byte, why you should do that, and how to apply that to a real programming
situation.</p>
<h2>More Ideas...</h2>
<p>What's that? Your new super high-tech futuristic cars have up to 16 available
features? No problem!</p>
<p>You can apply all the same techniques using 16 bit (= 2 byte) numbers, often
called integers.
<p>And so on... you could store 32 flags in a 32 bit (= 4 byte) integer (often
called a long integer).
<p>If you want another example of how to apply these techniques, I will tell you
about why I got the idea for this tutorial. I am working on several card games
by contract and my main task is to write a general, reusable ActiveX DLL which
can be used in all the card games. One of the features is to provide varied
animations on the cards, such as translation, spinning, resizing etc. Sometimes
you will want to apply more than one animation at once. To call the DLL to
perform an animation, you can write code as simple as this:
<p>StartAnimation (MOVE + SPIN + RESIZE)
<p>The DLL can then figure out which flags were passed to it all in one go.
Notice how you have just told the card to move, spin and resize in just one line
of code. So apart from the run time advantages of using flags, this also makes
it easier for programmers using the DLL.
<h4>Tutorial by Simon Price 31/07/01</h4>
<p><a href="mailto:Simon@VBgames.co.uk">Simon@VBgames.co.uk</a>
<p><a href="http://www.VBgames.co.uk">http://www.VBgames.co.uk</a>
</body>
</html>

