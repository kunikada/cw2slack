# Chatwork to Slack

2017年12月25日時点で動作確認済み

## Usage

`goodbye_chatwork` は改変したものを使う（submoduleで入ってる）

```sh
git submodule init && git submodule update
mkdir ./exports
mkdir ./converted
cd ./goodbye_chatwork
bundle install --path vendor/bundler
./bin/goodbye_chatwork -i example@example.com -p your_password -d ../exports -x room_id
cd ../
vi ./cw_users.json
node ./index.js
```

生成されたCSVファイルをSlackにインポートする
https://my.slack.com/services/import
ファイルは各チャンネルで手動で共有する

### cw_users.json

Slackにマッピングするための対応表

```js
[
  {
    // ChatWorkの利用者名
    "name": "ChatWork AccountName",
    // Uから始まるSlackのuserid
    "account": "U1A2B3C4D",
    // Chatworkの識別ID
    "id": "999999",
    // Slackのusername（メールアドレスのローカル部）
    "slackname": "slack.username"
  }
]
```

## LICENSE

MIT License
