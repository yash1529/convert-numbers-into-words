class num_2_word():
    
    """To convert given number into words"""
    def __init__(self,no,no_sys="INTERNATIONAL"):
        import sys
        self.no=no
        self.digit=len(str(no))#to calculate the no of digit
        self.no_sys=no_sys
        if self.no_sys=="INDIAN":
            if self.digit>20:
                print("GIVEN INTEGER SHOULD BE LESS THEN OR EQUAL TO 20 DIGITS")
                sys.exit()
            
        else:
            #International number system
            if self.digit>21:
                print("GIVEN INTEGER SHOULD BE LESS THEN OR EQUAL TO 21 DIGITS")
                sys.exit()
        #for now its onlyy available in INDIAN number system
      


    @staticmethod
    def multiple_10(no_digits):
        #to get mutiple of 10 for calculations
            x=10**(no_digits-1)
            return x

        
    def ones(self,x):
        """for 1 digit numbers"""
        one_digit=("ZERO","ONE","TWO","THREE","FOUR","FIVE","SIX","SEVEN","EIGHT","NINE")    
        return one_digit[x]


    def tens(self,x,digit):
        """for 2 digit numbers"""
        b4_19=("TEN","ELEVEN","TWELVE","THIRTEEN","FOURTEEN","FIFTEEN","SIXTEEN","SEVENTEEN","EIGHTEEN","NINETEEN")
        af_19=("","","TWENTY","THIRTY","FORTY","FIFTY","SIXTY","SEVENTY","EIGHTY","NINTY")

        if x%10==10 or x<20:
            #before 20 i.e [10-19]
            return b4_19[x - 10]
        else:
            first=x/self.multiple_10(digit)
            first=af_19[int(first)]#first digit

            second=x%self.multiple_10(2)

            if second==0:
                return first
            else:
                return first+" "+self.ones(int(second))


    def hundred(self,x,digit):
        """for 3 digits"""
        place="HUNDRED"
        first=x/self.multiple_10(digit)#hundred's place
        first=self.ones(int(first))+" "+place
        second=x%self.multiple_10(digit)
        if int(second) in range(0,10):
            if int(second)==0:
                pass
            else:
                return first+" "+self.ones(int(second))
        else:
            return first+" "+self.tens(int(second),2)
    
    def num_sys(self,pos):
        import sys
        """number system based on INTERNATIONAL or INDIAN"""
        #diff in place pos and digits||(4-1,5-2)(6-2,7-3)(8-3,9-4)......
        #default number system is international
        if self.no_sys=="INDIAN":
            position=("","","","THOUSAND","LAKH","CRORE","ARAB","KHARAB","NEEL","PADMA","SHANKH","MAHASHANKH")
            return position[pos]
        elif self.no_sys=="INTERNATIONAL":
            position=("","","","THOUSAND","MILLION","BILLION","TRILLION","QUADRILLION","QUINTILLION")
            return position[pos]
        else:
            print("Wrong input for numbersystem!")
            sys.exit()

    def Indian_no_sys_above_100(self,x,digit):
        """FOR 4 AND DIGIT AND MORE"""
        #INDIAN NUMBERING SYSTEM
        result=[]#empty list
        while (digit > 3):
            #it will run until digit is greater then 3
            if digit%2==0:
                #even place
                q,r=divmod(x,self.multiple_10(digit))
                x=r#re-assigning it to x
                pos=(digit+1)-((digit+1)//2)#index  position for num_system tuple
                result.append(self.ones(q)+" "+self.num_sys(pos))
                digit=len(str(x))#to update no of digits in a number
            else:
                #odd place
                f2no=int(str(x)[0:2])#first 2 numbers
                cal=(self.multiple_10(digit)//10) * f2no
                r=x%cal#remainder
                x=r#re-assigning it to x
                pos=digit-(digit//2)#index  position for num_system tuple
                result.append(self.tens(f2no,2)+" "+self.num_sys(pos))
                digit=len(str(x))#update no of digit
        else:
            if digit==3:
                result.append(self.hundred(x,3))
            elif digit==2:
                result.append((self.tens(x,2)))
            else:
                if x==0:
                    pass
                else:
                    result.append(self.ones(int(x)))
        result=" ".join(result)#after converting list into string
        return result


    def International_no_sys_above_100(self,x,digit):
        """For 4 digit and higher"""
        #INTERNATIONAL NUMBER SYSTEM
        result=[]#empyty list
        check_lst=(5,8,11,14,17,20)#for getting position in number 000,0*0,0*0,0*0,.... u can add more if need with difference of 3
        while digit>3:
            if digit%3==0:
                #multiple of 3 taking number in pair of 3
                f_3dig=int(str(x)[0:3]) #first 3 digits of number
                result.append(self.hundred(f_3dig,3)) #invoking hundred()
                pos=(digit//3)+1 #index position for num_system tuple
                result.append(self.num_sys(pos))
                r=x%(f_3dig*(self.multiple_10(digit)//100)) #remainder
                x=r #reassigning it to x
                digit=len(str(x)) #updating no of digits

            elif digit in check_lst:
                f_2dig=int(str(x)[0:2]) #first 2 digits of number
                result.append(self.tens(f_2dig,2)) #invoking tens()
                pos=((digit+1)//3)+1 #index position for num_system tuple
                result.append(self.num_sys(pos))
                r=x%(f_2dig*(self.multiple_10(digit)//10)) #remainder
                x=r #reassigning it to x
                digit=len(str(x)) #updating no of digits
            else:
                f_1dig=int(str(x)[0]) #first 1 digit of number
                result.append(self.ones(f_1dig)) #invoking ones()
                pos=((digit+1)//3)+2 #index position for num_system tuple
                result.append(self.num_sys(pos))
                r=x%(f_1dig*self.multiple_10(digit)) #remainder
                x=r #reassignment
                digit=len(str(x)) #update no of digits
        else:
            if digit==3:
                result.append(self.hundred(x,3))
            elif digit==2:
                result.append(self.tens(x,2))
            else:
                if x==0:
                    pass
                else:
                    result.append(self.ones(x))
        result=" ".join(result)#convert into string format
        return result


    def word(self):
        """To display final result"""
        if self.digit==1:
            return self.ones(self.no)
        elif self.digit==2:
            return self.tens(self.no,self.digit)
        elif self.digit==3:
            return self.hundred(self.no,self.digit)
        else:
            #after 999
            if self.no_sys=="INDIAN":
                return self.Indian_no_sys_above_100(self.no,self.digit)
            else:
                #INTERNATIONAL
                return self.International_no_sys_above_100(self.no,self.digit)

num = num_2_word(99999999,"INTERNATIONAL")
print(num.word())
