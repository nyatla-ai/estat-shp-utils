# Estat SHP Utils

CSV ファイルを正規化した形で SQLite データベースへ変換するためのツール集です。
`pandas` と `dbfread` が必要となります。プロジェクトを開発環境で利用す
る場合は次のようにインストールしてください。

```bash
pip install -e .
```

## ディレクトリ構成


- `estat_shp_utils/` - 汎用ライブラリ
- `app/` - コマンドラインスクリプト
- `dev/` - 開発用ファイル
- `doc/` - ドキュメント
- `sample/` - サンプルスクリプト

### 主なスクリプト

- `app/build_database.py` - 任意の CSV 群を 1 つのデータベースにまとめます。
- `app/import_r2ka.py` - `doc/R2KA_database_spec.md` のスキーマに従って R2KA 形式の CSV/DBF を取り込みます。

## 使用例

### 汎用 CSV 取り込み

```bash
python app/build_database.py CSVディレクトリ 出力.db
```

### R2KA CSV/DBF の取り込み

```bash
python app/import_r2ka.py 出力.db ./data/*.{csv,dbf}
```

`--encoding` オプションで CSV/DBF ファイルの文字コードを指定できます。既定値は
`cp932` です。

もし CSV 内に登録できないレコードが含まれている場合は、その内容を表示して処理を中断します。

