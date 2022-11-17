# bhaskarrepo
# bhaskarrepo
i have run intially in remontest class and i varified the result and i got successful result.

after that i have tried for spring boot with rest controller approch

the logic as below :


import java.util.Arrays;
import java.util.LinkedHashMap;
import java.util.List;
import java.util.Map;

import org.springframework.web.bind.annotation.GetMapping;

import com.companyname.springbootcrudrest.exception.RomenNumeralException;

public class RomenTest {

	@GetMapping("/roman-validate")
	public static String RomanNumerals(int num)   
	{  
	LinkedHashMap<String, Integer> romanNumerals = new LinkedHashMap<String, Integer>();  
	//storing roman letters and corresponding decimal values in HashMap  
	romanNumerals.put("M", 1000);  
	romanNumerals.put("CM", 900);  
	romanNumerals.put("D", 500);  
	romanNumerals.put("CD", 400);  
	romanNumerals.put("C", 100);  
	romanNumerals.put("XC", 90);  
	romanNumerals.put("L", 50);  
	romanNumerals.put("XL", 40);  
	romanNumerals.put("X", 10);  
	romanNumerals.put("IX", 9);  
	romanNumerals.put("V", 5);  
	romanNumerals.put("IV", 4);  
	romanNumerals.put("I", 1);  
	//variable for string the result  
	String result = "";  
	//loop iterate over Map  
	for(Map.Entry<String, Integer> entry : romanNumerals.entrySet())  
	{  
	int matches = num/entry.getValue();  
	result = result+repeat(entry.getKey(), matches);  
	num = num % entry.getValue();  
	}  
	return result;  
	}  
	public static String repeat(String s, int n)   
	{  
	if(s == null)   
	{  
	return null;  
	}  
	final StringBuilder sb = new StringBuilder();  
	for(int i = 0; i < n; i++)   
	{  
	sb.append(s);  
	}  
	//converts into string  
	return sb.toString();  
	}  
	//driver code  
	public static void main(String args[])   
	{  
	//prints roman numerals from 1 to 200 
		 Integer a[] = new Integer[] { 1, 4, 9, 90, 900, 1903, 1997, 4000, 0, -1 };
		 
         // Getting the list view of Array
         List<Object> list = Arrays.asList(a);
		
	for (int i = 1;i<=list.size();i++)   
	{  
		if(a[i]==0&& a[i]==-1)
		throw new RomenNumeralException("Romen numeral exception"+a[i]);
	System.out.println("i="+a[i]+" -> "+RomanNumerals(a[i]));  
	}  
	}  
}







o/p  :

i=4 -> IV
i=9 -> IX
i=90 -> XC
i=900 -> CM
i=1903 -> MCMIII
i=1997 -> MCMXCVII
i=4000 -> MMMM
i=0 -> 
i=-1 -> 
Exception in thread "main" java.lang.ArrayIndexOutOfBoundsException: 10
	at RomenTest.main(RomenTest.java:67)



    after that i have tried in rest api  define controller,service class as below:
    1.RomanNumeralToDigitController

    @GetMapping("/roman-validate")
	public static void romenValidate()
	{
	
	rs.validateRomen();
	  
		
	}
    2.RomenValidateService

     Integer a[] = new Integer[] { 1, 4, 9, 90, 900, 1903, 1997, 4000, 0, -1 };
	 
     // Getting the list view of Array
     List<Object> list = Arrays.asList(a);
	public void validateRomen() {
for (int i = 1;i<=list.size();i++)   
{  
	if(a[i]==0&& a[i]==-1)
	throw new RomenNumeralException("Romen numeral exception"+a[i]);
	System.out.println("i="+a[i]+" -> "+RomanNumerals(a[i])); 
	
}
RomanNumerals(int )
call from service class.


