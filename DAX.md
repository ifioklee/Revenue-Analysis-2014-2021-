# DAX Measures Documentation

## 1. Key Counts

### Number of Cities

``` dax
Number of cities = DISTINCTCOUNT(geo[City])
```

### Total Number of Countries

``` dax
Total number of Countries = DISTINCTCOUNT(Sales[Country])
```

### Total Number of Manufacturers

``` dax
Total Number of Manufacturers = DISTINCTCOUNT(manufacturer[ManufacturerID])
```

### Total Number of Products

``` dax
Total Number of Products = DISTINCTCOUNT('Product'[Product])
```

## 2. Revenue Measures

### Total Revenue

``` dax
total revenue = SUM(Sales[Revenue])
```

### Urban Revenue

``` dax
Urban Revenue =
CALCULATE(
    SUM(Sales[Revenue]),
    'Product'[Category] = "Urban"
)
```

### Urban Revenue Percentage

``` dax
Urban Revenue Percentage =
('DAX Formulas'[Urban Revenue] / 'DAX Formulas'[total revenue]) * 100
```
