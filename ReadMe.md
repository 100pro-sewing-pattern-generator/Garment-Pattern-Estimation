## MAC

### 本レポジトリのクローン
`git clone git@github.com:100pro-sewing-pattern-generator/Garment-Pattern-Estimation.git`

### Minicondaのインストール
`wget https://repo.anaconda.com/miniconda/Miniconda3-latest-MacOSX-arm64.sh`

### MinicondaのPATH設定
`export PATH="$HOME/miniconda3/bin:$PATH"`

### 環境設定
`conda create -n Garments python=3.9`
`conda activate Garments`

### 依存関係のインストール
`pip install -r requirements.txt`

### Garment-Pattern-Generatorレポジトリのクローン(Garment-Pattern-Estimationレポジトリと同じ階層)
`git clone git@github.com:100pro-sewing-pattern-generator/Garment-Pattern-Generator.git`

今の時点でファイル構造は
100pro

  -Garment-Pattern-Estimation

  -Garment-Pattern-Generator

### 評価データのダウンロード
https://zenodo.org/records/5267549

この中のtest.zipをダウンロードして解凍しtestフォルダを手に入れる

新しくGarments-datasetのフォルダをFinderで作り、その中にtestフォルダを置いとく

このGarments-datasetをGarment-Pattern-Estimationフォルダ, Garment-Pattern-Generatorフォルダと同じ場所に入れる

今の構造は

100pro
  -Garment-Pattern-Estimation
  -Garment-Pattern-Generator
  -Garments-dataset
    -test
      -dress_150
      -jacket_hood_sleevess_150
      ...

Garments-datasetフォルダをクリックしてCopy Pathを選択する

コピーされたものをGarment-Pattern-Estimationの中のsystem.jsonのdatasets_pathに貼り付ける

### 実行
`python nn/evaluation_scripts/on_test_set.py -sh models/att/att.yaml -st models/att/stitch_model.yaml --unseen --predict`

これで評価データの評価結果がoutputsフォルダに入る