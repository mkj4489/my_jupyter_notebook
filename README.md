# my_jupyter_notebook

- h : helpが表示される
- b : セルを増やす
- dd : セルを削除
- SHIFT + ENTER : セルの実行

- おまじない
import pandas as pd
import numpy as np
from matplotlib import pyplot as plt
%matplotlib inline

- csvファイルにヘッダー行がないものを読み込む場合
-- sample = pd.read_csv("sample.csv", header=None)

- 基本統計量を出力　train.describe()
- データの型を出力　train.info()
- 1つのカラムだけを出力　train["y"]
- yの平均　train["y"].mean()
- yの中央値　train["y"].median()
- yの値が150位上のデータを出力 train[train["y"]>=150]
- 曜日が月となっているデータを出力　train[train["week"]=="月"]
- 曜日が火となっているデータをyで昇順にして出力　train[train["week"]=="火"].sort_values(by="y")
- yとweekの２つのカラムを出力 train[["y","week"]]

- yの折れ線グラフを描く　train["y"].plot()
- yの折れ線グラフをもっと大きく描く　train["y"].plot(figsize=(12,4))
- 折れ線グラフにタイトルをつけて描く　ax = train["y"].plot(title="グラフ", figsize=(12,4))
- x軸に名前をつける　ax.set_xlabel("time")
- yのヒストグラムを描く　train["y"].plot.hist(grid=True)
- 平均値を表す縦線を描く　plt.axvline(x=train["y"].mean(), color="red")
- ヒストグラムをpngファイルとして保存する　plt.savefig("sample_fig.png")
- 箱ひげ図を描く　train[["y","week"]].boxplot(by="week")

- 各値が欠損値か否かを出力　train.isnull()
- 各列（カラム）にTrueが１つ以上あるかを出力　train.isnull().any()
- 各列カラムに欠損値をいくつあるかを数える　train.isnull().sum()
- 欠損値に０の値で補間する　train.fillna(0)
- 欠損値を削除する　train.dropna()
- precipitationの項目に、欠損値がないか確認　train["precipitation"].value_counts()

- 相関関係　どちらかが増えるともう一方も増える　正の相関　どちらかが増えるともう一方が減る　負の相関
- 0 相関関係がない　1 相関関係が強い
- 相関係数は、散布図を描いてみるとわかりやすい。
- ｙとtempperatureの相関係数を出す　train[["y","temperature"]].corr()
- 散布図を描く　train.plot.scatter(x="temperature", y="y", figsize=(5,5))

