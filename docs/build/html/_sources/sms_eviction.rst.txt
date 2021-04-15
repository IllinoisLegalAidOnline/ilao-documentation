======================
Eviction SMS Flow
======================

Workflow Tree
=================

Initial message
  Language prompt
    If Spanish, launch Spanish version (separate)
    
Overview message 

First name

Zip code

  In Illinois, 
    In Cook County, hand to Get Legal Help 
    Outside Cook County, CONTINUE
    
  Not in Illinois, offer to retry
    Link to LawHelp
    
Get Legal Issue (7 options)

  User replies More
    Show definitions
    Return to legal issue
    
  User replies 1
    User is asked if they have a summons
      If Yes, CONTINUE to matches
      If No, User is asked if they've received written notice
    
         If yes, CONTINUE to matches
         If no, user is asked if the landlord has threatened to evict
     
           If yes, CONTINUE to matches
           If no, EXIT to legal content
  
  User replies 2
     CONTINUE to matches
  
  User replies 3
     CONTINUE to matches
  
  User replies 4
   
     User is asked if the utilities were shut off because the tenant didn't pay the bills
   
        If yes, EXIT to legal content
        If no, continue to matches
          
  User replies 5 or 6,   
    
    Show nearest housing counselor
    Option to show all
    
      Loops through
      
  User replies 7, user gets exit message to Get Legal Help

Get Matches [Need API function built]

Ask user if they want to continue

  User says no
    Exits to Legal content

    
  Users says yes CONTINUE

Household prompt

  Household adult
  Household children
  
    Throw error if either is not numeric

Get last name

Get maiden names, if any

Get nicknames, if any

Get birth month

Get birth day

Get birth year

Validate birthdate

Ask user to confirm birthdate 
  If confirmed, CONTINIUE
  If not confirmed, go back to birth month

Start demographics

Get race
  If race = hispanic/latino, set ethnicity
  Otherwise, Get ethnicity

Get gender

Get marital status

Get language

Income prompt

Ask wages/salary
  Yes
    Ask frequency
      User replies 1,2,3,4 
        Get amount
        Validate and throw error if needed, else CONTINUE
      User replies anything else
        Throw error and allow them to correct  
      
  No
    CONTINUE
  Not sure
    Show help
  Numeric
    Validate and throw error if needed, else CONTINUE

Ask farming/self employment
  Yes
    Get amount
      Validate and throw error if needed, else CONTINUE
  No
    CONTINUE
  Not sure
    Show help
  Numeric
    Validate and throw error if needed, else CONTINUE

Ask benefits question (Yes, no, choices)
  Yes
    Ask for choice
      CONTINUE
  No
    CONTINUE to other payments
  Numeric choices
    CONTINUE
  Invalid data
    NEEDS WORK

For each benefit type selected:

  Ask amount
  Validate amount
  
    Ask user to retry if not numeric
    
  CONTINUE

Ask other payments question (Yes, no, choices)

  Yes
    Ask for choice
      CONTINUE
  No
    CONTINUE to other income
    
  Numeric choices
    CONTINUE

For each other payment type selected:

  Ask amount
  Validate amount
  
    Ask user to retry if not numeric
    
  CONTINUE

Ask if user has other income
  Yes
  
    Get amount
    Validate amount
    Re ask if invalid
    CONTINUE
    
  No
  
    CONTINUE
    
  Invalid input

Run income test (compare total income entered against standard)
 
  If user is over-income (80% of median income for household size)
 
    Inform user we can't complete intake
    Exit to legal information
 
  If user is not over-income CONTINUE  
  

Ask if current number is best to reach at

  YES
    CONTINUE
    
  NO
    Ask for valid number
    Validate number
    
      Valid => CONTINUE
      Invalid => Repeat

Get email address
Get street address
Get city

System call: Get contact type

  If we call client
  
    Get next date
    User says this work
    
      User picks from time slots
      
    User says this doesn't work
    
      Get next days
      
        User picks a day
        
          User picks from time slots
          
      No dates work
      
        Convert to you call us; CONTINUE to client calls

  Client calls
  Give confirmation message
  If user replies
  
    Give you are done message
  





