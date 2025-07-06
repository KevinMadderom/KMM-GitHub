[Uploadin'''
name: Kevin Madderom
email: kevin.madderom@ndus.edu
Writing functions and working with structures in Python
'''

def addClass(students, className, credits):      # Adds a class if it doesn't exist in the map
                                                 # returns true if class was added, false otherwise 
   if className in students:
      return False
   else:
      students[className] = credits
      return True
    
def updateClass(students, className, credits):   # Updates the credit of class if it exists in the map
                                                 # returns True if it updates, false otherwise
   if className in students:
      students[className] = credits
      return True
   else:
      return False
    
def totalCredits(students):                      # loops through students to sum all credit values then returns the sum 
   total = 0
   for credits in students.values():
      total += credits
   return total
    
def classesByDept(students, department):         # outer loop goes through the class names in the map
                                                 # the inner loop compares each character in department to the start of class name
                                                 # returns a list of class names in the department of original input
   result = []
   for className in students:
      deptStart = className.find(department)
      if deptStart == 0:
         result.append(className)
   return result
    
def classesByCredits(students, credits):         # Loops through the map to collect the names with the given credit number
   result = []
   for className in students:
      if students[className] == credits:
         result.append(className)
   return result
    
def isFullTime(students):                        # Loops through credit values and totals them, returns the total if >= 12
   total = 0
   for credit in students.values():
      total += credit
   return total >= 12
   
def canGraduate(students, requiredCredits=10):   # checks for enough credits, runs a loop to compare total credits to requiredCredits
   total = 0
   for credit in students.values():
      total += credit
      if total >= requiredCredits:
         return True
   return False
    
def upperLevelCredits(students):                  # This function splits the department and course number using loops
                                                  # outer loop goes through class names
                                                  # the inner loop finds the space between course and number
                                                  # final loop builds the number string
                                                  # checks if the course number is >= 300, then returns the total number of classes 
   total = 0
   for className in students:
      index = -1
      for i in range(len(className)):
         if className[i] == ' ':
            index = i
            break
      if index != -1 and index + 1 < len(className):
         stringClassNumber = ""
         for i in range(index + 1, len(className)):
            stringClassNumber += className[i]
         classNumber = int(stringClassNumber)
         
         if classNumber >= 300:
            total += students[className]
   return total

def main():

   students = {}

   print("Add CSCI 260:", addClass(students, "CSCI 260", 3))
   print("Add MATH 160:", addClass(students, "MATH 160", 4))
   print("Add CSCI 265:", addClass(students, "CSCI 265", 3))
   print("Add CSCI 260:", addClass(students, "CSCI 260", 3))
   print()
   print("Updating MATH 160 to 3 credits:", updateClass(students, "MATH 160", 3))
   print("Updating CSCI 260 to 2 credits:", updateClass(students, "CSCI 260", 2))
   print()
   print("Total credits: ", totalCredits(students))
   print()
   print("Classes in CSCI department: ", classesByDept(students, "CSCI"))
   print("Classes in MATH department: ", classesByDept(students, "MATH"))
   print()
   print("Classes with 4 credits: ", classesByCredits(students, 4))
   print("Classes with 3 credits: ", classesByCredits(students, 3))
   print()
   print("Is full time: ", isFullTime(students))
   print()
   addClass(students, "ENGL", 4)
   print("Is full time: ", isFullTime(students))
   print()
   print("Can graduate: ", canGraduate(students))
   print()
   addClass(students, "CSCI 360", 4)
   addClass(students, "HIST 380", 4)
   print("Upper-level credits: ", upperLevelCredits(students))

if __name__=="__main__":
   main()
   
   
         
    
    
    
g Prog6.py…]()
