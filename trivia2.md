Write the pseudocode of a function, which takes as input a String, and returns True if it is palindrome, or False otherwise.

> A palindrome is a word, phrase, or sequence that reads the same backwards as forwards

Example:
*  "savvas" => true
*  "pambos" => false


--------------------------- SOLUTION -----------------------------

function Palindrome(iString)
	end = len(iString) - 1
	for (i = 0, j = end; i < j; i++, j--)
		for (; iString[i] == “ ”; i++)				// Skip spaces from the left
		for (; iString[j] == “ ”; j--)					// Skip spaces from the right
		if (iString[i] != iString[j])
			return False
	return True

I’m assuming I don’t have to worry about the letter’s cases, otherwise I just need to make sure the comparison ignores the letter’s cases.

