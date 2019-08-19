Write, in pseudo-code, an efficient way of doing the following conversions and explain the complexity of the solution in big O notation

  1. Words only
  "Reverse this sentence" => "sentence this Reverse"
  
  2. Logical case
  "Reverse this sentence" => "Sentence this reverse"
  
  3. Logical dot anotation
  "Reverse this sentence." => "Sentence this reverse."
  
  4. Something more tricky
  "aaagggaaaiinnnnn" => "3a3g3a2i5n"



-------------------------------- SOLUTIONS ----------------------------


function Reverse(sentence, rMode)				// rMode: reverse mode requested (W, C, D)
	result = null
	end = len(sentence) - 1
	if (rMode != ‘W’)											// either Logical (W stands for Words only)
		sentence[0] += 32
	if (rMode == ‘D’)											// Logical dot annotation
		sentence[end] = null
		end--
	for (i = end; i > 0; i--)
		if (sentence[i] == “ ”)
			result += sentence[i + 1, end] + “ ” 
			i--
			for (; sentence[i] == “ ”; i--)	 // Eliminate additional spaces, sentences should use single spaces to separate words
			end = i
	result += sentence[i, end]
	if (rMode != ‘W’)
		result[0] -= 32
	if (rMode == ‘D’)
		result += ‘.’
	return result

I’m assuming sentence has already been validated to be a not-null words-only (that means at least one space) string, otherwise I just need to add conditions at the beginning to validate it’s a not-null string that complies with the requested rMode (first character is nothing but an upper case letter for either Logical and final character is nothing but a period for Logical dot annotation) or return error.



function Count(sentence)
	result = null
	end = len(sentence) - 1
	current = sentence[0]
	count = 1
	for (i = 1; i <= end; i++)
		if (sentence[i] == current)
			count++
		else
			result += string(count) + current
			current = sentence[i]
			count = 1
	result += string(count) + current
	return result

I’m assuming sentence has already been validated to be a not-null string, otherwise I just need to validate this at the beginning or return error.


All solutions have slightly less than O(n) complexity (worst case scenario is always n-1), because function Reverse skips 1 cicle every time it finds a space after a letter and function Count skips the first character’s cicle, but as far as official notation goes, they all have O(n) complexity.
