# No_Broker
My python code shown below




{
 "cells": [
  {
   "cell_type": "code",
   "execution_count": 1,
   "metadata": {},
   "outputs": [],
   "source": [
    "import pandas as pd\n",
    "import numpy as np\n",
    "import matplotlib.pyplot as plt\n",
    "import seaborn as sns\n",
    "%matplotlib inline"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 2,
   "metadata": {},
   "outputs": [],
   "source": [
    "from sklearn.datasets import load_boston\n",
    "boston = load_boston()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 3,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>CRIM</th>\n",
       "      <th>ZN</th>\n",
       "      <th>INDUS</th>\n",
       "      <th>CHAS</th>\n",
       "      <th>NOX</th>\n",
       "      <th>RM</th>\n",
       "      <th>AGE</th>\n",
       "      <th>DIS</th>\n",
       "      <th>RAD</th>\n",
       "      <th>TAX</th>\n",
       "      <th>PTRATIO</th>\n",
       "      <th>B</th>\n",
       "      <th>LSTAT</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>0</th>\n",
       "      <td>0.00632</td>\n",
       "      <td>18.0</td>\n",
       "      <td>2.31</td>\n",
       "      <td>0.0</td>\n",
       "      <td>0.538</td>\n",
       "      <td>6.575</td>\n",
       "      <td>65.2</td>\n",
       "      <td>4.0900</td>\n",
       "      <td>1.0</td>\n",
       "      <td>296.0</td>\n",
       "      <td>15.3</td>\n",
       "      <td>396.90</td>\n",
       "      <td>4.98</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1</th>\n",
       "      <td>0.02731</td>\n",
       "      <td>0.0</td>\n",
       "      <td>7.07</td>\n",
       "      <td>0.0</td>\n",
       "      <td>0.469</td>\n",
       "      <td>6.421</td>\n",
       "      <td>78.9</td>\n",
       "      <td>4.9671</td>\n",
       "      <td>2.0</td>\n",
       "      <td>242.0</td>\n",
       "      <td>17.8</td>\n",
       "      <td>396.90</td>\n",
       "      <td>9.14</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2</th>\n",
       "      <td>0.02729</td>\n",
       "      <td>0.0</td>\n",
       "      <td>7.07</td>\n",
       "      <td>0.0</td>\n",
       "      <td>0.469</td>\n",
       "      <td>7.185</td>\n",
       "      <td>61.1</td>\n",
       "      <td>4.9671</td>\n",
       "      <td>2.0</td>\n",
       "      <td>242.0</td>\n",
       "      <td>17.8</td>\n",
       "      <td>392.83</td>\n",
       "      <td>4.03</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>3</th>\n",
       "      <td>0.03237</td>\n",
       "      <td>0.0</td>\n",
       "      <td>2.18</td>\n",
       "      <td>0.0</td>\n",
       "      <td>0.458</td>\n",
       "      <td>6.998</td>\n",
       "      <td>45.8</td>\n",
       "      <td>6.0622</td>\n",
       "      <td>3.0</td>\n",
       "      <td>222.0</td>\n",
       "      <td>18.7</td>\n",
       "      <td>394.63</td>\n",
       "      <td>2.94</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4</th>\n",
       "      <td>0.06905</td>\n",
       "      <td>0.0</td>\n",
       "      <td>2.18</td>\n",
       "      <td>0.0</td>\n",
       "      <td>0.458</td>\n",
       "      <td>7.147</td>\n",
       "      <td>54.2</td>\n",
       "      <td>6.0622</td>\n",
       "      <td>3.0</td>\n",
       "      <td>222.0</td>\n",
       "      <td>18.7</td>\n",
       "      <td>396.90</td>\n",
       "      <td>5.33</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "      CRIM    ZN  INDUS  CHAS    NOX     RM   AGE     DIS  RAD    TAX  \\\n",
       "0  0.00632  18.0   2.31   0.0  0.538  6.575  65.2  4.0900  1.0  296.0   \n",
       "1  0.02731   0.0   7.07   0.0  0.469  6.421  78.9  4.9671  2.0  242.0   \n",
       "2  0.02729   0.0   7.07   0.0  0.469  7.185  61.1  4.9671  2.0  242.0   \n",
       "3  0.03237   0.0   2.18   0.0  0.458  6.998  45.8  6.0622  3.0  222.0   \n",
       "4  0.06905   0.0   2.18   0.0  0.458  7.147  54.2  6.0622  3.0  222.0   \n",
       "\n",
       "   PTRATIO       B  LSTAT  \n",
       "0     15.3  396.90   4.98  \n",
       "1     17.8  396.90   9.14  \n",
       "2     17.8  392.83   4.03  \n",
       "3     18.7  394.63   2.94  \n",
       "4     18.7  396.90   5.33  "
      ]
     },
     "execution_count": 3,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "boston_df = pd.DataFrame(boston.data)\n",
    "# Convert index to column name using dataset feature names \n",
    "boston_df.columns = boston.feature_names\n",
    "boston_df.head()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 4,
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "<class 'pandas.core.frame.DataFrame'>\n",
      "RangeIndex: 506 entries, 0 to 505\n",
      "Data columns (total 13 columns):\n",
      "CRIM       506 non-null float64\n",
      "ZN         506 non-null float64\n",
      "INDUS      506 non-null float64\n",
      "CHAS       506 non-null float64\n",
      "NOX        506 non-null float64\n",
      "RM         506 non-null float64\n",
      "AGE        506 non-null float64\n",
      "DIS        506 non-null float64\n",
      "RAD        506 non-null float64\n",
      "TAX        506 non-null float64\n",
      "PTRATIO    506 non-null float64\n",
      "B          506 non-null float64\n",
      "LSTAT      506 non-null float64\n",
      "dtypes: float64(13)\n",
      "memory usage: 51.5 KB\n"
     ]
    }
   ],
   "source": [
    "boston_df.info()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 5,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>CRIM</th>\n",
       "      <th>ZN</th>\n",
       "      <th>INDUS</th>\n",
       "      <th>CHAS</th>\n",
       "      <th>NOX</th>\n",
       "      <th>RM</th>\n",
       "      <th>AGE</th>\n",
       "      <th>DIS</th>\n",
       "      <th>RAD</th>\n",
       "      <th>TAX</th>\n",
       "      <th>PTRATIO</th>\n",
       "      <th>B</th>\n",
       "      <th>LSTAT</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>count</th>\n",
       "      <td>506.000000</td>\n",
       "      <td>506.000000</td>\n",
       "      <td>506.000000</td>\n",
       "      <td>506.000000</td>\n",
       "      <td>506.000000</td>\n",
       "      <td>506.000000</td>\n",
       "      <td>506.000000</td>\n",
       "      <td>506.000000</td>\n",
       "      <td>506.000000</td>\n",
       "      <td>506.000000</td>\n",
       "      <td>506.000000</td>\n",
       "      <td>506.000000</td>\n",
       "      <td>506.000000</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>mean</th>\n",
       "      <td>3.593761</td>\n",
       "      <td>11.363636</td>\n",
       "      <td>11.136779</td>\n",
       "      <td>0.069170</td>\n",
       "      <td>0.554695</td>\n",
       "      <td>6.284634</td>\n",
       "      <td>68.574901</td>\n",
       "      <td>3.795043</td>\n",
       "      <td>9.549407</td>\n",
       "      <td>408.237154</td>\n",
       "      <td>18.455534</td>\n",
       "      <td>356.674032</td>\n",
       "      <td>12.653063</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>std</th>\n",
       "      <td>8.596783</td>\n",
       "      <td>23.322453</td>\n",
       "      <td>6.860353</td>\n",
       "      <td>0.253994</td>\n",
       "      <td>0.115878</td>\n",
       "      <td>0.702617</td>\n",
       "      <td>28.148861</td>\n",
       "      <td>2.105710</td>\n",
       "      <td>8.707259</td>\n",
       "      <td>168.537116</td>\n",
       "      <td>2.164946</td>\n",
       "      <td>91.294864</td>\n",
       "      <td>7.141062</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>min</th>\n",
       "      <td>0.006320</td>\n",
       "      <td>0.000000</td>\n",
       "      <td>0.460000</td>\n",
       "      <td>0.000000</td>\n",
       "      <td>0.385000</td>\n",
       "      <td>3.561000</td>\n",
       "      <td>2.900000</td>\n",
       "      <td>1.129600</td>\n",
       "      <td>1.000000</td>\n",
       "      <td>187.000000</td>\n",
       "      <td>12.600000</td>\n",
       "      <td>0.320000</td>\n",
       "      <td>1.730000</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>25%</th>\n",
       "      <td>0.082045</td>\n",
       "      <td>0.000000</td>\n",
       "      <td>5.190000</td>\n",
       "      <td>0.000000</td>\n",
       "      <td>0.449000</td>\n",
       "      <td>5.885500</td>\n",
       "      <td>45.025000</td>\n",
       "      <td>2.100175</td>\n",
       "      <td>4.000000</td>\n",
       "      <td>279.000000</td>\n",
       "      <td>17.400000</td>\n",
       "      <td>375.377500</td>\n",
       "      <td>6.950000</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>50%</th>\n",
       "      <td>0.256510</td>\n",
       "      <td>0.000000</td>\n",
       "      <td>9.690000</td>\n",
       "      <td>0.000000</td>\n",
       "      <td>0.538000</td>\n",
       "      <td>6.208500</td>\n",
       "      <td>77.500000</td>\n",
       "      <td>3.207450</td>\n",
       "      <td>5.000000</td>\n",
       "      <td>330.000000</td>\n",
       "      <td>19.050000</td>\n",
       "      <td>391.440000</td>\n",
       "      <td>11.360000</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>75%</th>\n",
       "      <td>3.647423</td>\n",
       "      <td>12.500000</td>\n",
       "      <td>18.100000</td>\n",
       "      <td>0.000000</td>\n",
       "      <td>0.624000</td>\n",
       "      <td>6.623500</td>\n",
       "      <td>94.075000</td>\n",
       "      <td>5.188425</td>\n",
       "      <td>24.000000</td>\n",
       "      <td>666.000000</td>\n",
       "      <td>20.200000</td>\n",
       "      <td>396.225000</td>\n",
       "      <td>16.955000</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>max</th>\n",
       "      <td>88.976200</td>\n",
       "      <td>100.000000</td>\n",
       "      <td>27.740000</td>\n",
       "      <td>1.000000</td>\n",
       "      <td>0.871000</td>\n",
       "      <td>8.780000</td>\n",
       "      <td>100.000000</td>\n",
       "      <td>12.126500</td>\n",
       "      <td>24.000000</td>\n",
       "      <td>711.000000</td>\n",
       "      <td>22.000000</td>\n",
       "      <td>396.900000</td>\n",
       "      <td>37.970000</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "             CRIM          ZN       INDUS        CHAS         NOX          RM  \\\n",
       "count  506.000000  506.000000  506.000000  506.000000  506.000000  506.000000   \n",
       "mean     3.593761   11.363636   11.136779    0.069170    0.554695    6.284634   \n",
       "std      8.596783   23.322453    6.860353    0.253994    0.115878    0.702617   \n",
       "min      0.006320    0.000000    0.460000    0.000000    0.385000    3.561000   \n",
       "25%      0.082045    0.000000    5.190000    0.000000    0.449000    5.885500   \n",
       "50%      0.256510    0.000000    9.690000    0.000000    0.538000    6.208500   \n",
       "75%      3.647423   12.500000   18.100000    0.000000    0.624000    6.623500   \n",
       "max     88.976200  100.000000   27.740000    1.000000    0.871000    8.780000   \n",
       "\n",
       "              AGE         DIS         RAD         TAX     PTRATIO           B  \\\n",
       "count  506.000000  506.000000  506.000000  506.000000  506.000000  506.000000   \n",
       "mean    68.574901    3.795043    9.549407  408.237154   18.455534  356.674032   \n",
       "std     28.148861    2.105710    8.707259  168.537116    2.164946   91.294864   \n",
       "min      2.900000    1.129600    1.000000  187.000000   12.600000    0.320000   \n",
       "25%     45.025000    2.100175    4.000000  279.000000   17.400000  375.377500   \n",
       "50%     77.500000    3.207450    5.000000  330.000000   19.050000  391.440000   \n",
       "75%     94.075000    5.188425   24.000000  666.000000   20.200000  396.225000   \n",
       "max    100.000000   12.126500   24.000000  711.000000   22.000000  396.900000   \n",
       "\n",
       "            LSTAT  \n",
       "count  506.000000  \n",
       "mean    12.653063  \n",
       "std      7.141062  \n",
       "min      1.730000  \n",
       "25%      6.950000  \n",
       "50%     11.360000  \n",
       "75%     16.955000  \n",
       "max     37.970000  "
      ]
     },
     "execution_count": 5,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "boston_df.describe()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 6,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "Index(['CRIM', 'ZN', 'INDUS', 'CHAS', 'NOX', 'RM', 'AGE', 'DIS', 'RAD', 'TAX',\n",
       "       'PTRATIO', 'B', 'LSTAT'],\n",
       "      dtype='object')"
      ]
     },
     "execution_count": 6,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "boston_df.columns"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 7,
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "shape of X =  (506, 13)  shape of y =  (506,)\n"
     ]
    }
   ],
   "source": [
    "X = boston_df\n",
    "y = boston.target\n",
    "print( \"shape of X = \", X.shape, \" shape of y = \", y.shape )"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 8,
   "metadata": {},
   "outputs": [],
   "source": [
    "from sklearn.model_selection import train_test_split"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 9,
   "metadata": {},
   "outputs": [],
   "source": [
    "X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.3, random_state=42)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 11,
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "(354, 13) (354,)\n",
      "(152, 13) (152,)\n"
     ]
    }
   ],
   "source": [
    "print(X_train.shape, y_train.shape )\n",
    "print(X_test.shape, y_test.shape)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 12,
   "metadata": {},
   "outputs": [],
   "source": [
    "# Import LinearRegression from Scikit Learn library\n",
    "from sklearn.linear_model import LinearRegression"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 13,
   "metadata": {},
   "outputs": [],
   "source": [
    "lm = LinearRegression()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 14,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "LinearRegression(copy_X=True, fit_intercept=True, n_jobs=1, normalize=False)"
      ]
     },
     "execution_count": 14,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# Train/fit lm on the training data.\n",
    "lm.fit(X_train, y_train)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 15,
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "Coefficients: \n",
      " [-1.32774155e-01  3.57812335e-02  4.99454423e-02  3.12127706e+00\n",
      " -1.54698463e+01  4.04872721e+00 -1.07515901e-02 -1.38699758e+00\n",
      "  2.42353741e-01 -8.69095363e-03 -9.11917342e-01  1.19435253e-02\n",
      " -5.48080157e-01]\n"
     ]
    }
   ],
   "source": [
    "# The coefficients\n",
    "print('Coefficients: \\n', lm.coef_)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 16,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>Coeffecient</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>CRIM</th>\n",
       "      <td>-0.132774</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>ZN</th>\n",
       "      <td>0.035781</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>INDUS</th>\n",
       "      <td>0.049945</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>CHAS</th>\n",
       "      <td>3.121277</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>NOX</th>\n",
       "      <td>-15.469846</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>RM</th>\n",
       "      <td>4.048727</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>AGE</th>\n",
       "      <td>-0.010752</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>DIS</th>\n",
       "      <td>-1.386998</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>RAD</th>\n",
       "      <td>0.242354</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>TAX</th>\n",
       "      <td>-0.008691</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>PTRATIO</th>\n",
       "      <td>-0.911917</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>B</th>\n",
       "      <td>0.011944</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>LSTAT</th>\n",
       "      <td>-0.548080</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "         Coeffecient\n",
       "CRIM       -0.132774\n",
       "ZN          0.035781\n",
       "INDUS       0.049945\n",
       "CHAS        3.121277\n",
       "NOX       -15.469846\n",
       "RM          4.048727\n",
       "AGE        -0.010752\n",
       "DIS        -1.386998\n",
       "RAD         0.242354\n",
       "TAX        -0.008691\n",
       "PTRATIO    -0.911917\n",
       "B           0.011944\n",
       "LSTAT      -0.548080"
      ]
     },
     "execution_count": 16,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "coeffecients = pd.DataFrame(lm.coef_,X.columns)\n",
    "coeffecients.columns = ['Coeffecient']\n",
    "coeffecients"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 17,
   "metadata": {},
   "outputs": [],
   "source": [
    "predictions = lm.predict(X_test)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "#Create a scatterplot of the real test values versus the predicted values.\n",
    "plt.scatter(y_test, predictions, s=5)\n",
    "plt.xlabel('Real Price')\n",
    "plt.ylabel('Predicted Prices')\n",
    "plt.title( \"Real vs Predicted Housing Prices\")"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "lm.score(X_test, y_test)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "# calculate these metrics by hand!\n",
    "from sklearn import metrics\n",
    "\n",
    "print('MAE:', metrics.mean_absolute_error(y_test, predictions))\n",
    "print('MSE:', metrics.mean_squared_error(y_test, predictions))\n",
    "print('RMSE:', np.sqrt(metrics.mean_squared_error(y_test, predictions)))"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "# print the intercept\n",
    "print(lm.intercept_)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 25,
   "metadata": {},
   "outputs": [
    {
     "ename": "SyntaxError",
     "evalue": "invalid syntax (<ipython-input-25-475fdf76f510>, line 1)",
     "output_type": "error",
     "traceback": [
      "\u001b[1;36m  File \u001b[1;32m\"<ipython-input-25-475fdf76f510>\"\u001b[1;36m, line \u001b[1;32m1\u001b[0m\n\u001b[1;33m    matpltlib.((y_test-predictions),bins=50);\u001b[0m\n\u001b[1;37m              ^\u001b[0m\n\u001b[1;31mSyntaxError\u001b[0m\u001b[1;31m:\u001b[0m invalid syntax\n"
     ]
    }
   ],
   "source": [
    "matpltlib((y_test-predictions),bins=50);"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": []
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": []
  }
 ],
 "metadata": {
  "kernelspec": {
   "display_name": "Python 3",
   "language": "python",
   "name": "python3"
  },
  "language_info": {
   "codemirror_mode": {
    "name": "ipython",
    "version": 3
   },
   "file_extension": ".py",
   "mimetype": "text/x-python",
   "name": "python",
   "nbconvert_exporter": "python",
   "pygments_lexer": "ipython3",
   "version": "3.6.4"
  }
 },
 "nbformat": 4,
 "nbformat_minor": 2
}
