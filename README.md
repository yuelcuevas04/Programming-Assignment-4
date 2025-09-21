# Programming-Assignment-4
# ECE Board Exam Problem

## 1.)
    import pandas as pd
    
    eceboards = pd.read_csv('board2.csv')
    eceboards
   ### a.)
    Instru = eceboards.loc[(eceboards['Track']=='Instrumentation') & (eceboards['Hometown']=='Luzon') & (eceboards['Electronics'] >70),['Name','GEAS','Electronics']]
    print(Instru)
  ### b)
    eceboards['Average'] = eceboards[['Math','Electronics','GEAS','Communication']].mean(axis=1)
    
    Mindy = eceboards.loc[(eceboards['Hometown']=='Mindanao') & (eceboards['Gender']=='Female') & (eceboards['Average']>=55),['Name','Track','Electronics','Average']]
    print(Mindy)


## 2.)
    import matplotlib.pyplot as plt
    
    plt.figure(figsize=(5,5))
    plt.bar(eceboards['Track'], eceboards['Average'])
    
    plt.figure(figsize=(5,5))
    plt.bar(eceboards['Gender'], eceboards['Average'])
    
    plt.figure(figsize=(5,5))
    plt.bar(eceboards['Hometown'], eceboards['Average'])
