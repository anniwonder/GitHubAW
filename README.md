### 30th April 2020


### GitHub Bikeshare refactoring branch
This branch is used to work on the bikeshare.py code project
After changes in the code were made, the file was being commited and merged with the master

### Adding code to display raw data to lines 166 to 212 in bikeshare.py
def display_raw_data(df):
    '''display raw data on screen'''
    n=5
    print(df.head(n))
    while True:
        more=input("\nWould you like to see more raw data?  Please eneter 'yes' or 'no'\n").lower()
        if more =='no':
            break
        elif more=='yes':
            n=n+5
            print(df.iloc[n-5:n, :])
        else:
            print('\nInvalid input')

def main():
    print("\nHello! Let\'s explore some US bikeshare data!")
    while True:
        while True:
            raw_or_stats=input("\nWould you like to see raw data or stats?   Please enter 'raw' or 'stats'\n").lower()
            if raw_or_stats=='raw':
                city, month, day = get_filters()
                df = load_data(city, month, day)
                display_raw_data(df)
                break
            elif raw_or_stats =='stats':
                new_path, txt_file, files_saved_to = createfilepath()
                while True:
                    all_cities=input("Would you like to stats of all three cities?  Please enter 'yes' or 'no'\n").lower()
                    if all_cities=='yes':#the user like to view all cities
                            #calculates various stats of all three cities
                        calculate_all(new_path,txt_file)
                        break
                    elif all_cities=='no':
                        city, month, day = get_filters()
                        df = load_data(city, month, day)
                        single_city(city,df,new_path,txt_file)
                        break
                    else:
                        print('Invalid input.\n')
                print(files_saved_to)
                txt_file.close()
                break
            else:
                print('\nInvalid input')
        restart = input("Would you like to restart? Please enter 'yes' or 'no'.\n").lower()
        if restart.lower() != 'yes':
            break

### Acknowledgements
Udacity Data Analytics Programming Nano Degree lectures and videos
