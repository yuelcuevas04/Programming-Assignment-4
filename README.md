# Programming-Assignment-4
# ECE Board Exam Problem

**1.)** In the First part of the programming assignment, it is required to create the specified dataframes following the given format and structure. Each dataframe should be constructed carefully to match the sample layout provided, and follows the column names, data types, and values.

    import pandas as pd    #Library of pandas as pd
    
    eceboards = pd.read_csv('board2.csv') #opens and reads the file 'board2.csv' and transfers the dataframe to 'eceboards'
    eceboards

<img width="504" height="800" alt="image" src="https://github.com/user-attachments/assets/024a0736-28b1-45bd-ad21-2988cc8685eb" />

    
**a.)** The Instru dataframe contains the Name, GEAS, and Electronics > 70, with a specific track of Instrumentation and a specific hometown of Luzon. This will show a dataframe of students with a track record of Instrumentation and a hometown of Luzon who passed the particular condition of Electronics > 70.

    Instru = eceboards.loc[(eceboards['Track']=='Instrumentation') &   #A condition that prioritizes the 'Instrumentation' Track 
                        (eceboards['Hometown']=='Luzon') &             #A condition that prioritizes the 'Luzon' Hometown
                        (eceboards['Electronics'] >70),                #Conditional statement showing only students with Electronics >70
                        ['Name','GEAS','Electronics']]                 #Shows a dataframe with Name, GEAS, Electronics as columns
    print(Instru)                                                      #Prints the dataframe: Instru

<img width="160" height="66" alt="image" src="https://github.com/user-attachments/assets/f2b9a90c-e40a-48b6-9261-4c0ab35a6c06" />

    
**b.)** The Mindy dataframe contains the Name, Track, Electronics, and Average >=55, with specifics of hometown in Mindanao and a Female gender. This will show a dataframe of students from Mindanao and a gender of female with an average score in all subjects greater than 55.

    eceboards['Average'] = eceboards[['Math','Electronics','GEAS','Communication']].mean(axis=1) #Solves the mean/average of different scores of students in different subjects.
    
    Mindy = eceboards.loc[(eceboards['Hometown']=='Mindanao') &     #A condition that prioritizes students from 'Mindanao' only
                        (eceboards['Gender']=='Female') &           #A condition that proprotizes students that are 'Female'
                        (eceboards['Average']>=55),                 #Conditional statement that shows only students with Average>=55
                        ['Name','Track','Electronics','Average']]   #Shows a dataframe with Name, Track, Electronics, and Average as columns
    print(Mindy)                                                    #Prints the dataframe: Mindy

<img width="295" height="96" alt="image" src="https://github.com/user-attachments/assets/9481dafa-d2f9-4076-809a-53eb586c1bba" />


**2.)** The second part of the programming assignment features a visualization showing the features that contribute to the average grade of students and how it is affected by their track in college, their gender, or their hometowns. This displays a bar graph with specific features, average being constant, and Track, Gender, and Hometown will be changed and displayed differently through different graphs.

    import matplotlib.pyplot as plt                                #imports the Library matplot.lib.pyplot as plt
    
    plt.figure(figsize=(5,5))                                      #Code for the figure size of the bar graph
    plt.bar(eceboards['Track'], eceboards['Average'])              #Shows a graph that has a x-axis of Track and y-axis of Average

<img width="353" height="379" alt="image" src="https://github.com/user-attachments/assets/2f86247a-f05d-4bff-a79f-c93a1cb23286" />


    plt.figure(figsize=(5,5))                                      #Code for the figure size of the bar graph
    plt.bar(eceboards['Gender'], eceboards['Average'])             #Shows a graph that has a x-axis of Gender anf y-axis of Average

<img width="304" height="374" alt="image" src="https://github.com/user-attachments/assets/93ac5351-71fb-43bd-b9f7-a5debe10618d" />

    
    plt.figure(figsize=(5,5))                                      #Code for the figure size of the bar graph
    plt.bar(eceboards['Hometown'], eceboards['Average'])           #Shows a graph that has a x-axis of Hometown anf y-axis of Average

<img width="375" height="371" alt="image" src="https://github.com/user-attachments/assets/dfa186c5-6ef6-4f58-8341-f73bbac70d46" />

