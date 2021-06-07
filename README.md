
GIGO(Garbage In Garbage Out)

머신러닝에서 제일 중요한 요소중 하나는 깨끗한 데이터를 사용 하는 것

똑같은 데이터세트를 사용하더라도, 데이터의 전처리나, 분석 방법 등에 따라서 성능이 굉장히 많이 차이 난다.


# 사용할 데이터셋 다운로드 하기

import os

import tarfile

import urllib.request


DOWNLOAD_ROOT = "https://raw.githubusercontent.com/ageron/handson-ml2/master/"

HOUSING_PATH = os.path.join("datasets", "housing") # 디렉토리 설정하기 - /기본 경로/datasets/housing

HOUSING_URL = DOWNLOAD_ROOT + "datasets/housing/housing.tgz" # 다운로드 할 파일의 URL


def fetch_housing_data(housing_url= HOUSING_URL, housing_path= HOUSING_PATH):

os.makedirs(housing_path, exist_ok= True) # 디렉토리 만들기

tgz_path = os.path.join(housing_path, "housing.tgz") # 파일의 경로

urllib.request.urlretrieve(housing_url, tgz_path) # URL로 지정한 파일을 다운로드

housing_tgz = tarfile.open(tgz_path) # 다운 받은 파일 열기

housing_tgz.extractall(path= housing_path) # 압축 파일(housing.tgz) 압축 풀기

housing_tgz.close() # 파일 닫기


fetch_housing_data()


# 다운 받은 데이터셋(csv) 파일을 pandas 데이터 프레임으로 만들기

import pandas as pd


def load_housing_data(housing_path=HOUSING_PATH, filename="housing.csv"):

csv_path = os.path.join(housing_path, filename) # os.path.join("/datasets/housing", "housing.csv") -> /datasets/housing/housing.csv

return pd.read_csv(csv_path) # 데이터 프레임 리턴


housing = load_housing_data()

housing.head()


housing.info()


housing.describe()


import matplotlib.pyplot as plt

housing.hist(bins=50, figsize=(20, 15)) # 데이터 프레임에서 히스토그램을 확인하면 전체 수치데이터에 대한 빈도수가 등장.

plt.show()

﻿
