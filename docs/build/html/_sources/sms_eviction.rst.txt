======================
Eviction SMS Flow
======================

ERP Workflow Tree

Initial message
  Language prompt
    If Spanish, launch Spanish version (separate)
    
Overview message 

First name

Zip code

  In Illinois, 
    In Cook County, hand to Get Legal Help [needs build]
    Outside Cook County, CONTINUE
    
  Not in Illinois, offer to retry
    Link to LawHelp
    
Get Legal Issue

  User replies More
    Show definitions
    Return to legal issue
    
  User replies with a legal issue, CONTINUE
  User replies with a non legal housing issue
  
    Show nearest housing counselor
    Option to show all
    
      Loops through
      
    Returns to household questions [is this the correct behavior]

NOTE:  Moved Household Questions

Get Matches [Need API function built]

Ask user if they want to continue

  User says no
    Exits to Legal content
    Offer counseling options
    
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
    Get amount
      Validate and throw error if needed, else CONTINUE
      
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

Ask if current number is best to reach at

  YES
    CONTINUE
    
  NO
    Ask for valid number
    Need to validate number
    
      Valid => CONTINUE
      Invalid => Repeat

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
  
  




