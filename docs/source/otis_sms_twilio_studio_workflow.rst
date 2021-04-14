==============================
OTIS Master Twilio Workflow
==============================

This documents the flow of the OTIS Master flow in Twilio Studio.

The general flow of the OTIS SMS tool is:

* Get the user's first name
* Get the user's zip code; this validates that the user is in Illinois. If the user:

  * If the user is not in Illinois, they are directed to LawHelp.org
  * If the user is in Illinois, they are offered a menu of options for help (currently limited to unemployment, food stamps/TANF, or other). **Picking other, exits the user to the website application.**
  
    * If the user picks unemployment or food stamps/tanf (Guided navigation needs to be dropped in here)
     
      * Number of adults is collected
      * Number of children is collected 
      * The basic income calculation is computed and the user is asked a Y/N question if their household income exceeds our base threshold. If the user indicates Yes, they are exited to the website application.
      
    * If the user indicates they are not over-income and are matched to an organization, they are told who they matched to and given the option to continue to a full application. ** If they say no, they are exited to Get Legal Help on the website**  If they say yes:
    
      * They are prompted to enter their last name
      * They are asked if they have any maiden names. If they enter Yes, they are asked to provide them. If they enter no, they are taken to the next question. If they enter other text, that is treated as their maiden name.
      * They are asked if they have any nicknames. If they enter Yes, they are asked to provide them. If they enter no, they are taken to the next question. If they enter other text, that is treated as their nickname.
      * The user is then prompted to enter their birthday:
      
        * The month is collected; full month names, abbreviations, and numbers are all supported
        * The day is collected; only values between 1 - 31 are collected
        * The year is collected; 2 and 4 digit years are supported.
      
      * The user is then taken through demographics questions:
      
        * Race
        * Ethnicity
        * Gender
        * Marital status
        * Language preference
        
      * The user is then taken to a series of income questions. For each money input, the system validates that the user entered a number and redirects back to the question if they do not.
      
        * Do they have wages/salary - if they indicate yes or wages or salary, they are asked to provide the amount.    
        * Do they have farming or self-employment income - if they indicate yes or wages or salary, they are asked to provide the amount.  
        * Do they have one or more government benefits; entering any number or partial text will result in a match. The user is then cycled through all the benefits they have to provide an amount. Government benefits include: TANF, Veterans benefits (including disability), unemployment, SSI, Social security.
        * Do they have one or more other payments; entering any number or partial text will result in a match. The user is then cycled through all the payments they have to provide an amount. Payment types include:  private disability payments, alimony, child support, workers compensation, pension/retirement income, and investment income.
        * Do they have any other income? If they respond yes, they are asked for the amount.
        * Once income is collected, we collect contact information:
        
          * Is this there best contact number (if they say no, they are prompted to add a number)
          * What is their email address?
          * What is their street address
          * What city?
          
        * Next it processes the confirmation:
        
          * If the user needs to call the program, it exits with the "please call" message.
          * If the user needs to schedule a callback:
          
            * The system provides the range of available times and the first available day.
            * If the user is okay with that day, they are provided a list of time slots
            * If the user is not okay with that day, they are provided a list of alternate days.
            
              * If none of the dates work, the user is prompted to text 0 which will convert it to a "please call"
              * If one of the dates work, they are provided with a list of time slots to pick one.
            
            * Once the user picks a time slot, the data is transferred and they are given their confirmation text message. 
          
  
  