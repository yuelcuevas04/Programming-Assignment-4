# Programming-Assignment-4
# ECE Board Exam Problem

**1.)** In the First part of the programming assignment, it is required to create the specified dataframes following the given format and structure. Each dataframe should be constructed carefully to match the sample layout provided, and follows the column names, data types, and values.

    import pandas as pd    #Library of pandas as pd
    
    eceboards = pd.read_csv('board2.csv') #opens and reads the file 'board2.csv' and transfers the dataframe to 'eceboards'
    eceboards

<img width="518" height="798" alt="image" src="https://github.com/user-attachments/assets/3645e3c8-2ab8-4b44-a634-5cac62015d52" />


**a.)** The Instru dataframe contains the Name, GEAS, and Electronics > 70, with a specific track of Instrumentation and a specific hometown of Luzon. This will show a dataframe of students with a track record of Instrumentation and a hometown of Luzon who passed the particular condition of Electronics > 70.

    Instru = eceboards.loc[(eceboards['Track']=='Instrumentation') &   #A condition that prioritizes the 'Instrumentation' Track 
                        (eceboards['Hometown']=='Luzon') &             #A condition that prioritizes the 'Luzon' Hometown
                        (eceboards['Electronics'] >70),                #Conditional statement showing only students with Electronics >70
                        ['Name','GEAS','Electronics']]                 #Shows a dataframe with Name, GEAS, Electronics as columns
    print(Instru)                                                      #Prints the dataframe: Instru

<img width="232" height="91" alt="image" src="https://github.com/user-attachments/assets/73d8a335-ca6d-49e0-92cf-cc66577cd9df" />

**b.)** The Mindy dataframe contains the Name, Track, Electronics, and Average >=55, with specifics of hometown in Mindanao and a Female gender. This will show a dataframe of students from Mindanao and a gender of female with an average score in all subjects greater than 55.

    eceboards['Average'] = eceboards[['Math','Electronics','GEAS','Communication']].mean(axis=1) #Solves the mean/average of different scores of students in different subjects.
    
    Mindy = eceboards.loc[(eceboards['Hometown']=='Mindanao') &     #A condition that prioritizes students from 'Mindanao' only
                        (eceboards['Gender']=='Female') &           #A condition that proprotizes students that are 'Female'
                        (eceboards['Average']>=55),                 #Conditional statement that shows only students with Average>=55
                        ['Name','Track','Electronics','Average']]   #Shows a dataframe with Name, Track, Electronics, and Average as columns
    print(Mindy)                                                    #Prints the dataframe: Mindy

<img width="404" height="127" alt="image" src="https://github.com/user-attachments/assets/ae18e44c-47c0-40ac-9988-26e660cf4d18" />

**2.)** The second part of the programming assignment features a visualization showing the features that contribute to the average grade of students and how it is affected by their track in college, their gender, or their hometowns. This displays a bar graph with specific features, average being constant, and Track, Gender, and Hometown will be changed and displayed differently through different graphs.

     import matplotlib.pyplot as plt                         #Library of matplotlib.pyplot as plt
     
     avg = eceboards.groupby('Track')['Average'].mean()      #Solves for the average mean grouped by Tracks
     
     plt.bar (avg.index, avg.values)                         #Categorize the average mean values of the Tracks
     plt.ylabel('Mean')                                      #Displays the label of Mean in y-axis
     plt.xlabel('Tracks')                                    #Displays the label of Tracks in x-axis
     plt.show()                                              #Shows the Bar Graph of mean average grouped based on Tracks

<img width="739" height="533" alt="image" src="https://github.com/user-attachments/assets/cc7449d7-c0ca-45f3-966a-fec5476b3c53" />


     avg = eceboards.groupby('Gender')['Average'].mean()      #Solves for the average mean grouped by Gender
    
     plt.bar (avg.index, avg.values)                         #Categorize the average mean values of the Gender
     plt.ylabel('Mean')                                      #Displays the label of Mean in y-axis
     plt.xlabel('Gender')                                    #Displays the label of Gender in x-axis
     plt.show()                                              #Shows the Bar Graph of mean average grouped based on Gender

<img width="716" height="539" alt="image" src="https://github.com/user-attachments/assets/beaf6f36-d5b6-4995-9c58-c8d0bde9f496" />


     avg = eceboards.groupby('Hometown')['Average'].mean()      #Solves for the average mean grouped by Hometown
     
     plt.bar (avg.index, avg.values)                            #Categorize the average mean values based on Hometown
     plt.ylabel('Mean')                                         #Displays the label of Mean in y-axis
     plt.xlabel('Hometown')                                     #Displays the label of Hometown in x-axis
     plt.show()                                                 #Shows the Bar Graph of mean average grouped based on Hometown

<img width="745" height="537" alt="image" src="https://github.com/user-attachments/assets/66c13b2a-df55-41d8-a794-6196461bf186" />




