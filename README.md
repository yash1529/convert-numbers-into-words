# convert-numbers-into-words
This module help to convert postive integers into string as per International as well as Indian numbering system.

#BASIC INFORMATION:

*Max integer input is upto 20 digits
*As per Indian numbering system its highest position is Mahashank i.e(10**19)
*As per International numbering system its highest position is QUINTILLION i.e(10**19)
*1st arg is postive number,2nd arg is numbering system i.e international and Indian
*Default numbering system is International
*For educational purpose and office purpose.


#Example 1:
Given input number : x=123456
import num_to_word
z=num_to_word(x).word()
print(z)
#output : one hundred twenty three thousand four hundred fifty six

#Example 2:
Given input number : x=123456
import num_to_word
z=num_to_word(x,no_sys="INDIAN").word()
print(z)
#output : one lakh twenty three thousand four hundred fifty six

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~            Thanks alot for using it ;)          ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
