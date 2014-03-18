package com.vishalaksh.radixconverter;

/**
 * The class BaseConversion Converts A valid base to another Base less than or equal to 36.
 * The Base from 2 to 36 contains all elements from 0-9 and A-Z (Capital only Allowed) and 
 * in the program extracts each original Character and finds the index which in turn returns 
 * the Equivalent word in the KeyNodes and the original is first Converted to Decimal and 
 * then to the required base. A Validate function checks if the original value has all the 
 * digits of the original said base type. Note : base 1 is not valid.
 * 
 */
import java.io.*;

public class BaseConversion {
	static BufferedReader br = new BufferedReader(new InputStreamReader(
			System.in));

	static String Orig_Num = "", Conv_Num = "",
			KeyNodes = "0123456789ABCDEFGHIJKLMNOPQRSTUVWXYZ";
	static int Orig_Base = 0, Conv_Base = 0, Deci_Num = 0, p = 0, flag = 0;

	static int fDeci_Num = 0;
	static int q = 0;
	static int precision = 5;
	static String fOrig_Num = "", fConv_Num = "";

	/**
	 * Method to input data from the user.
	 */
	private void input() throws Exception {

		do {
			System.out
					.print("Enter the ORIGINAL NUMBER: ");
			Orig_Num = br.readLine();
			Orig_Num = Orig_Num.toUpperCase();

			do {
				flag = 0;
				System.out.print("Enter the ORIGINAL Base : ");
				Orig_Base = Integer.parseInt(br.readLine());
				if ((Orig_Base < 2) || (Orig_Base > 36)) {
					System.out.println("Invalid Base");
					flag = 1;
				}
			} while (flag == 1);

			if (!validate(Orig_Num, Orig_Base)) {
				System.out.println("Invalid Character Of Valid Base Found");
				flag = 1;
			}

		} while (flag == 1);

		do {
			flag = 0;
			System.out.print("Enter the CONVERSION Base : ");
			Conv_Base = Integer.parseInt(br.readLine());
			if ((Conv_Base < 2) || (Conv_Base > 36)) {
				System.out.println("Invalid Base");
				flag = 1;
			}
		} while (flag == 1);
	}

	/**
	 * @param Num
	 *            the number entered by the user
	 * @param Base
	 *            the base of the number
	 * @return false if the given number is not possible in the given base
	 */
	private boolean validate(String Num, int Base) {
		for (int i = 0; i < Num.length(); i++)
			if (KeyNodes.indexOf(Num.charAt(i)) >= Base)
				return false;
		return true;
	}

	void breaknum() {
		fOrig_Num = Orig_Num.substring(Orig_Num.indexOf(".") + 1).trim();
		Orig_Num = Orig_Num.substring(0, Orig_Num.indexOf(".")).trim();
	}

	/**
	 * convers the number into base 10
	 */
	private void decimalConvert() {
		p = Orig_Num.length() - 1;
		for (int i = 0; i < Orig_Num.length(); i++)
			Deci_Num += ((KeyNodes.indexOf(Orig_Num.charAt(i))) * (Math.pow(
					Orig_Base, p--)));
	}

	/**
	 * convers the number into base 10
	 */
	private void fDecimalConvert() {
		double decimal_number = 0;
		q = 1;
		for (int i = 0; i < fOrig_Num.length(); i++)
			decimal_number += ((KeyNodes.indexOf(fOrig_Num.charAt(i))) * (Math
					.pow(Orig_Base, (-1) * (q++))));

		String s = String.valueOf(decimal_number);

		s = s.substring(s.indexOf(".") + 1,
				Math.min(s.indexOf(".") + 1 + precision, s.length()));

		fDeci_Num = Integer.valueOf(s);

	}

	/**
	 * converts the number(in base 10) into the given base
	 */
	private void baseConvert() {
		do {
			Conv_Num = (KeyNodes.charAt(Deci_Num % Conv_Base) + Conv_Num);
			Deci_Num /= Conv_Base;
		} while (Deci_Num >= 1);
	}

	/**
	 * converts the number(in base 10) into the given base
	 */
	private void fBaseConvert() {
		int len = getlen(fDeci_Num);

		int count = 0;
		do {
			fConv_Num = (fConv_Num + KeyNodes.charAt((int) (fDeci_Num
					* Conv_Base / (Math.pow(10, len)))));

			fDeci_Num = (int) ((fDeci_Num * Conv_Base) % (Math.pow(10, len)));
			count++;

		} while (fDeci_Num > 0 && count < precision);
	}

	private int getlen(int fDeci_Num2) {
		int i = 0;
		while (fDeci_Num2 > 0) {
			fDeci_Num2 = fDeci_Num2 / 10;
			i++;
		}
		return i;
	}

	public static void main(String args[]) throws Exception {

		BaseConversion obj = new BaseConversion();
		obj.input();
		boolean isFloating = false;

		if (Orig_Num.contains(".")) {
			obj.breaknum();
			isFloating = true;

		}

		// convert the number into base 10
		obj.decimalConvert();
		obj.fDecimalConvert();
		// if the final base is not 10, then again convert base 10 into the
		// final base
		if (!(Conv_Base == 10)) {
			obj.baseConvert();
			obj.fBaseConvert();
		}

		if (isFloating) {
			// print the results
			System.out.println("Original  Number : " + Orig_Num + "."
					+ fOrig_Num + " :: Base : " + Orig_Base);
		} else {
			System.out.println("Original  Number : " + Orig_Num + " :: Base : "
					+ Orig_Base);
		}
		if (!(Conv_Base == 10))
			System.out.println("Converted Number : " + Conv_Num + "."
					+ fConv_Num + " :: Base : " + Conv_Base);
		else
			System.out.println("Converted Number : " + Deci_Num + "."
					+ fDeci_Num + " :: Base : " + Conv_Base);
	}
}
