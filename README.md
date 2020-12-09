# **The Process is divided in 4 Steps**
- [x] Cleaning the Data
- [x] Removing Outliers
- [x] EDA on cleaned dataset
- [x] Model Building

# **Cleaning The Data-Set**

**Filling NaN values with Median for Train Dataset**

```python
fill_na_train = train_df['Stall_no'].median()
train_df['Stall_no'].fillna(fill_na_train, inplace=True)

fill_na_train = train_df['Discount_avail'].median()
train_df['Discount_avail'].fillna(fill_na_train, inplace=True)

fill_na_train = train_df['charges_1'].median()
train_df['charges_1'].fillna(fill_na_train, inplace=True)

fill_na_train = train_df['charges_2 (%)'].median()
train_df['charges_2 (%)'].fillna(fill_na_train, inplace=True)

fill_na_train = train_df['Minimum_price'].median()
train_df['Minimum_price'].fillna(fill_na_train, inplace=True)

fill_na_train = train_df['Maximum_price'].median()
train_df['Maximum_price'].fillna(fill_na_train, inplace=True)

fill_na_train = train_df['Selling_Price'].median()
train_df['Selling_Price'].fillna(fill_na_train, inplace=True)
```

**Checking all values were filled**

```python
train_df.isnull().sum()
```
**Output:**
```Product_id            0
Stall_no              0
instock_date          0
Market_Category       0
Customer_name       211
Loyalty_customer      0
Product_Category      0
Grade                 0
Demand                0
Discount_avail        0
charges_1             0
charges_2 (%)         0
Minimum_price         0
Maximum_price         0
Selling_Price         0
dtype: int64
```

**Filling NaN values with Median for Test Dataset**

```python
fill_na_test = test_df['Stall_no'].median()
test_df['Stall_no'].fillna(fill_na_test, inplace=True)

fill_na_test = test_df['charges_1'].median()
test_df['charges_1'].fillna(fill_na_test, inplace=True)

fill_na_test = test_df['charges_2 (%)'].median()
test_df['charges_2 (%)'].fillna(fill_na_test, inplace=True)

fill_na_test = test_df['Minimum_price'].median()
test_df['Minimum_price'].fillna(fill_na_test, inplace=True)
```
**Checking all values were filled**

```python
test_df.isnull().sum()
```

**Output:**
```
Product_id           0
Stall_no             0
instock_date         0
Market_Category      0
Customer_name       53
Loyalty_customer     0
Product_Category     0
Grade                0
Demand               0
Discount_avail       0
charges_1            0
charges_2 (%)        0
Minimum_price        0
Maximum_price        0
dtype: int64
```

<br><br>

# **Removing The Outlier**
 
Removed Outliers by Using IQR method:
```python
def outlier_removal(column):
    sorted(column)
    Q1, Q3 = np.percentile(column, [25, 75])
    
    IQR = Q3 - Q1
    
    lower_value = Q1 - (1.5 * IQR)
    upper_value = Q3 + (1.5 * IQR)
    return lower_value, upper_value
```
