# The task of string compression
It has been slightly modified, but the algorithm remains the same.
Write a method that accepts a string containing letters and returns a new string in which the same consecutive characters are replaced by a number + a letter if there are more than one characters.
If a character occurs once, it remains unchanged.
# Here is the solution with comments on C#
public string complexLetter(string str)
        {
            string resultingString = string.Empty;
            int nuberOfSameLetter = 0;
            var lastLetter = str[0];
            for (int i = 0; i < str.Length; i++)
            {
                if (lastLetter == str[i])
                {
                    nuberOfSameLetter++;
                    continue; // if last letter == current leter continue append 1, while values are equal 
                }
                if (lastLetter != str[i])
                {
                    resultingString = nuberOfSameLetter > 1 ? 
                    resultingString + nuberOfSameLetter.ToString() + lastLetter.ToString() : 
                    resultingString + lastLetter.ToString(); //append one char or number char + char(if nuber > 1) 
                    nuberOfSameLetter = 0; //Values are not equal now
                }
                nuberOfSameLetter++;
                lastLetter = str[i];
            }
            // last char 
            if (lastLetter == str[str.Length - 1] && nuberOfSameLetter != 1)
            {
                resultingString = resultingString + nuberOfSameLetter.ToString() + lastLetter.ToString();
            }
            else
            {
                resultingString += str[str.Length - 1];
            }
            return resultingString;
        }
