# なにかAWSで動かしてみよう！勉強会
- [kickoff資料 (6/27)](https://drive.google.com/file/d/13UmDCY0It_p6k5LcnncdKVXB5xfEkQYv/view?usp=sharing)
- [1回目資料 (6/27)](https://drive.google.com/file/d/13Vtnb3wu9G2vnnJ2a7LoDRNizRwdMbnO/view?usp=sharing)
- [2回目資料 (7/12)](https://drive.google.com/file/d/14IaxcRxUXRfw2uOcvdqJFo8Iy5ukA-la/view)
- [3回目資料 (7/26)](https://drive.google.com/file/d/14KKmSNkCeAlNTSBny_Nj0gFUQmhcV2c9/view)

## 3回目課題(GitHub Actionsでコンテナイメージをビルドでしてデプロイする)に関する情報
### コンテナイメージのビルドと実行（Dockerfileを作ってから）
```shell
# jarのビルド
mvn clean package
# コンテナイメージのビルド
docker build -t hello-app .
# ローカルリポジトリに登録されていることの確認(hello-appがあること)
docker images hello-app
# コンテナの実行
docker run -p 7001:7001 --name hello-app --rm hello-app
```

## 2回目課題(GitHub Actionsでビルドでしてjarをデプロイする)に関する情報
### sampleアプリのビルドと起動
```shell
# ビルド
mvn clean package
# 起動
java -jar target/hello-app.jar
# REST APIへのリクエスト
curl -X GET localhost:7001/api/hello
```
### pom.xmlの追加設定のsnippet
```xml
	<distributionManagement>
		<repository>
			<id>github</id>
			<name>GitHub Packages</name>
			<url>https://maven.pkg.github.com/@your_account@/@your_repository@</url>
		</repository>
	</distributionManagement>
```
※snippetの右上のアイコンをクリックするとコピーできる
