# insert_data_into_csv
#This code is represent the insert data into specific column compare with othre column exsiting data in csv file fill the other remaining values into same csv file using python 


    import pandas as pd
    
    # Read the CSV file
    #if your
    file_path = 'update_finalallvar.csv'
    df = pd.read_csv(file_path)
    x = df['ConnID'].isin(['0243036094a806cc'])
    new_rows = pd.DataFrame(columns=df.columns)
    connid_list = ['0243035D33A50A28','0243035d734d170c','0243035e4645863b','0243035D734DD5BC','0243035e46467db9']
    for connid in connid_list:
        if df.query(f'ConnID == "{connid}"') is None:
            print("connid is not found")
        else:
            empty_index = df.query(f'ConnID == "{connid}"').index
            empty_index = empty_index[0]
            print(empty_index)
            print(df.loc[empty_index, 'transcript'])
            print(df.loc[empty_index, 'CQ_SCORE'])
            df.loc[empty_index, 'transcript'] = f"transcript enter here...{empty_index}"
            print("connid is found")
    
    df.to_csv(file_path, index=False)
