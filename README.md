# Python-Practice
Recently written python code used to test some functions. Function included are encryption and decryption functions. Function that makes a list of tuples for reoccurring letters in a string. Last function adds up total hours spent studying for a class.
###################################################################################
#NAME: Ash Mahein                                                                 #
#ID: 11463887                                                                     #
#DATE: 01/23/17                                                                   #
#Collaborators:                                                                   #
#                                                                                 #
#                                                                                 #
#                                                                                 #
#                                                                                 #
#                                                                                 #
#                                                                                 #
###################################################################################
import operator
# This function encrypts two given strings by matching each character to one another.
def cryptDict(s1, s2):
    # empty dictionary.
    dictionary = {}
    # for loop that allows user to parse through the strings putting them into the dictionary
    for x in range(0, len(s1)):
        dictionary[s1[x]] = s2[x]
        # returns the dictionary
    return dictionary
    pass


# decryption function that takes two parameters. One is a dictionary from the encryption
# function. The second parameter is a string.
def decrypt(cDict, S):
    # empty string.
    dCry = ''
    # for loop that allows user to parse through the string switching out charcters that are
    # in the string.
    for c in range(0, len(S)):
        # switches out the letters, decrypting the message.
        if cDict.get(S[c], S[c]):
            dCry = dCry + cDict.get(S[c], S[c])
    # returns the decrypted messages.
    return dCry
    pass


# testDecrypt is a function that test the above functions to see if they work.
def testDecrypt():
    # The functions used below aide in testing to see if my code works.
    cDict = cryptDict('abc', 'xyz')
    revcDict = cryptDict('xyz', 'abc')
    tests = "Now I know my abc's"
    answer = "Now I know my xyz's"

    if decrypt(cDict, tests) != answer:
        return False
    if decrypt(revcDict, decrypt(cDict, tests)) != "Now I know mb abc's":
        return False
    if decrypt(cDict, '') != '':
        return False
    if decrypt(cryptDict('', ''), 'abc') != 'abc':
        return False
    return True
    pass


########################################################################################################################

# charCount fucntion takes in one input paramater which is a string.
def charCount(S):
    # the count variable is an empty list.
    counter = []
    # for loop that traverses the string S and counts the occurence of characters.
    for x in S:
        # conditional statement that parses through the string. It skips all space characters when counting the number
        # of characters.
        if x != ' ':
            counter.append((x, S.count(x)))
    # gets rid of all duplicate characters.
    counter = list(set(counter))
    # sorts the list of tuples alphabetically.
    counter.sort()
    counter.sort(key=lambda tup: tup[1])
    # returns the list.
    return counter

# Test function belows tests to see if the above function will work, given a certain set of strings with numbers and
# repeating letters.
def testCharCount():
    # example one
    string1 = "Wood Chuck Could Chuck Wood"
    answer1 = [('l', 1), ('W', 2), ('c', 2), ('h', 2), ('k', 2), ('C', 3), ('d', 3), ('u', 3), ('o', 5)]
    # example two
    string2 = "Sally Sells Seashells"
    answer2 = [('h', 1), ('y', 1), ('a', 2), ('S', 3), ('e', 3), ('s', 3), ('l', 6)]
    # example three
    string3 = "CoDiNg CaN gEt cRaZy iN CpTs 355"
    answer3 = [('3', 1), ('D', 1), ('E', 1), ('R', 1), ('T', 1), ('Z', 1), ('c', 1), ('o', 1), ('p', 1), ('s', 1),
               ('t', 1), ('y', 1), ('5', 2), ('a', 2), ('g', 2), ('i', 2), ('C', 3), ('N', 3)]
    # example given by professor.
    sentence = "Cpts355 --- Assign1"
    totalChar = charCount(sentence)
    exAnswer = [('1', 1), ('3', 1), ('A', 1), ('C', 1), ('g', 1), ('i', 1), ('n', 1), ('p', 1), ('t', 1), ('5', 2),
                ('-', 3), ('s', 3)]


    # the conditionals below check to see if the answers are correct and if they aren't then a False is returned.
    if exAnswer != totalChar:
        return False
    if charCount(string1) != answer1:
        return False
    if charCount(string2) != answer2:
        return False
    if charCount(string3) != answer3:
        return False
    else:
        return True

########################################################################################################################

def dictAddup(d):
    dictionary = {}
    sum302 = 0
    sum322 = 0
    sum355 = 0

    for i in d:
        sum302 += d[i]["302"]
        sum322 += d[i]["322"]
        sum355 += d[i]["355"]
    dictionary["302"] = sum302
    dictionary["322"] = sum322
    dictionary["355"] = sum355

    return dictionary

def testAddup():

    testCase1 = {"Monday":{"302": 2, "322": 1, "355": 2}, "Tuesday": {"302": 2, "322": 3, "355": 1},
                 "Thursday": {"302": 1, "322": 1, "355": 1}, "Friday": {"302": 1, "322": 1, "355": 1},
                 "Saturday": {"302": 1, "322": 1, "355": 1}}
    testCaseAnswer1 = {'302': 7, '322': 7, '355': 6}

    testCase2 = {"Monday":{"302": 1, "322": 1, "355": 1}, "Tuesday": {"302": 1, "322": 1, "355": 1},
                 "Thursday": {"302": 1, "322": 1, "355": 1}, "Friday": {"302": 1, "322": 1, "355": 1},
                 "Saturday": {"302": 1, "322": 1, "355": 1}, "Sunday": {"302": 1, "322": 1, "355": 1}}
    testCaseAnswer2 = {'302': 6, '322': 6, '355': 6}

    testCase3 = {"Tuesday": {"302": 3, "322": 7, "355": 1}, "Thursday": {"302": 1, "322": 1, "355": 4},
                 "Friday": {"302": 5, "322": 9, "355": 1}, "Saturday": {"302": 3, "322": 1, "355": 2},
                 "Sunday": {"302": 1, "322": 2, "355": 1}}
    testCaseAnswer3 = {'302': 13, '322': 20, '355': 9}


    if dictAddup(testCase1) != testCaseAnswer1:
        return False
    if dictAddup(testCase2) != testCaseAnswer2:
        return False
    if dictAddup(testCase3) != testCaseAnswer3:
        return False
    else:
        return True


