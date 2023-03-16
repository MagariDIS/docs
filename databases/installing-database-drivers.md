# databases/installing-database-drivers

## データベース
新しいデータベース ドライバーを、接続先のデータストアごとに Python DB-API データベース ドライバーと SQLAlchemy ダイアレクトをインストールする必要があります。

サポートされているデータベースとPython 標準ライブラリの一部である SQLite を除いて、データベースへの接続にバンドルされていません。
メタデータ データベースとして使用するデータベースに必要なパッケージと、スーパーセットを介してアクセスするデータベースに接続するために必要なパッケージをインストールする必要があります。

推奨パッケージのリスト

| データベース	| PyPI パッケージ	| 接続文字列 |
|-------------|----------------|-----------|
| Amazon AWS アテナ AWSが提供するS3にあるデータファイルに対してクエリを実行することの出来るサービス |pip install "PyAthenaJDBC>1.0.9、pip install "PyAthena>1.2.0	| awsathena+rest://{aws_access_key_id}:{aws_secret_access_key}@athena.{region_name}.amazonaws.com/{|
| Amazon AWS DynamoDB	AWSが提供するフルマネージド NoSQL データベース| pip install "PyDynamoDB>=0.4.2	| dynamodb://{access_key_id}:{secret_access_key}@dynamodb.{region_name}.amazonaws.com?connector=superset|
| Amazon AWS Redshift レッドシフト AWSが提供するデータウェアハウスサービス | pip install sqlalchemy-redshift	| redshift+psycopg2://<userName>:<DBPassword>@<AWS End Point>:5439/<Database Name>|
| Apache Drill アパッチ ドリル | pip install sqlalchemy-drill	| drill+sadrill:// For JDBC drill+jdbc:// |
| Apache Solr ソーラー 全文検索エンジン	| pip install sqlalchemy-solr	| solr://{username}:{password}@{hostname}:{port}/{server_path}/{collection} |
| Apache Spark スパーク 大規模データ処理のための統合分析エンジン  | SQL	pip install pyhive	| hive://hive@{hostname}:{port}/{database} |
| Ascend.io Ascend.ioが提供する Data Pipeline Automation | pip install impyla	| ascend://{username}:{password}@{hostname}:{port}/{database}?auth_mechanism=PLAIN;use_ssl=true |
| MS SQL Server | pip install pymssql	| mssql+pymssql://UserName@presetSQL:TestPassword@presetSQL.database.windows.net:1433/TestSchema |
| MS SQL Server ODBC | pip install pyodbc | mssql+pyodbc:///?odbc_connect=Driver%3D%7BODBC+Driver+17+for+SQL+Server%7D%3BServer%3Dtcp%3A%3Cmy_server%3E%2C1433%3BDatabase%3Dmy_datasbase%3BUid%3Dmy_user_name%3BPwd%3Dmy_password%3BEncrypt%3Dyes%3BConnection+Timeout%3D30 | 
| ビッグクエリ	| pip install sqlalchemy-bigquery	| bigquery://{project_id} |
| Elasticsearch エラスティックサーチ	| pip install elasticsearch-dbapi	| elasticsearch+http://{user}:{password}@{host}:9200/ |
| Google スプレッドシート	| pip install shillelagh[gsheetsapi]	| gsheets:// |
| firebolt ファイアボルト |	pip install firebolt-sqlalchemy	| firebolt://{username}:{password}@{database} or firebolt://{username}:{password}@{database}/{engine_name} |
| IBM Db2	| pip install ibm_db_sa	| db2+ibm_db:// |
| MySQL	無料で利用できるRDBツール | pip install mysqlclient	| mysql://<UserName>:<DBPassword>@<Database Host>/<Database Name> |
| オラクル	| pip install cx_Oracle	| oracle:// |
| PostgreSQL 無料で利用できるRDBツール | pip install psycopg2	| postgresql://<UserName>:<DBPassword>@<Database Host>/<Database Name> |
| SAP HANA ハナ (High-performance ANalytic Appliance) は、データをディスクに保存せずに、メモリーに保存するマルチモデルデータベース	| pip install hdbcli sqlalchemy-hana or pip install apache-superset[hana]	| hana://{username}:{password}@{host}:{port} |
| snowflake スノーフレーク	| pip install snowflake-sqlalchemy	| snowflake://{user}:{password}@{account}.{region}/{database}?role={role}&warehouse={warehouse} |
| SQLite 無料で利用できるRDBツール	| 追加のライブラリは不要	| sqlite:// |
  
他のデータベースが SQLAlchemy ダイアレクトと Python ドライバーがサポートされていることに注意してください。
「sqlalchemy + (データベース名)」というキーワードでGoogle検索すると、適切な場所にたどり着くことができます。 👍
