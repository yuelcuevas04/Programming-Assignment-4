# Programming-Assignment-4
# ECE Board Exam Problem

**1.)** In the First part of the programming assignment, it is required to create the specified dataframes following the given format and structure.Each dataframe should be constructed carefully to match the sample layout provided, and follows the column names, data types, and values.

    import pandas as pd    #Library of pandas as pd
    
    eceboards = pd.read_csv('board2.csv') #opens and reads the file 'board2.csv' and transfers the dataframe to 'eceboards'
    eceboards
    
**a.)** The Instru dataframe contains the Name, GEAS, and Electronics > 70, with a specific track of Instrumentation and a specific hometown of Luzon. This will show a dataframe of students with a track record of Instrumentation and a hometown of Luzon who passed the particular condition of Electronics > 70.

    Instru = eceboards.loc[(eceboards['Track']=='Instrumentation') &   #A condition that prioritizes the 'Instrumentation' Track 
                        (eceboards['Hometown']=='Luzon') &             #A condition that prioritizes the 'Luzon' Hometown
                        (eceboards['Electronics'] >70),                #Conditional statement showing only students with Electronics >70
                        ['Name','GEAS','Electronics']]                 #Shows a dataframe with Name, GEAS, Electronics as columns
    print(Instru)                                                      #Prints the dataframe: Instru
    
**b.)** The Mindy dataframe contains the Name, Track, Electronics, and Average >=55, with specifics of hometown in Mindanao and a Female gender. This will show a dataframe of students from Mindanao and a gender of female with an average score in all subjects greater than 55.

    eceboards['Average'] = eceboards[['Math','Electronics','GEAS','Communication']].mean(axis=1) #Solves the mean/average of different scores of students in different subjects.
    
    Mindy = eceboards.loc[(eceboards['Hometown']=='Mindanao') &     #A condition that prioritizes students from 'Mindanao' only
                        (eceboards['Gender']=='Female') &           #A condition that proprotizes students that are 'Female'
                        (eceboards['Average']>=55),                 #Conditional statement that shows only students with Average>=55
                        ['Name','Track','Electronics','Average']]   #Shows a dataframe with Name, Track, Electronics, and Average as columns
    print(Mindy)                                                    #Prints the dataframe: Mindy
    

**2.)** The second part of the programming assignment features a visualization showing the features that contribute to the average grade of students and how it is affected by their track in college, their gender, or their hometowns. This displays a bar graph with specific features, average being constant, and Track, Gender, and Hometown will be changed and displayed differently through different graphs.

    import matplotlib.pyplot as plt                                #imports the Library matplot.lib.pyplot as plt
    
    plt.figure(figsize=(5,5))                                      #Code for the figure size of the bar graph
    plt.bar(eceboards['Track'], eceboards['Average'])              #Shows a graph that has a x-axis of Track and y-axis of Average
    
    plt.figure(figsize=(5,5))                                      #Code for the figure size of the bar graph
    plt.bar(eceboards['Gender'], eceboards['Average'])             #Shows a graph that has a x-axis of Gender anf y-axis of Average
    
    plt.figure(figsize=(5,5))                                      #Code for the figure size of the bar graph
    plt.bar(eceboards['Hometown'], eceboards['Average'])           #Shows a graph that has a x-axis of Hometown anf y-axis of Average
