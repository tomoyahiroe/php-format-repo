# 教材内コードのフォーマット用レポジトリです。

## 目的

インデントの崩れているPHPのコードをPSR12に準拠した形にフォーマットすることが目的です。

誰がインデント修正作業をしても同じ結果が得られます。

## 前提

- VScode の使用を前提としています。

- VScode ユーザなら個人の設定に左右されずに全員共通のフォーマットが走るようにしています。

- composer をインストールしていることを前提としています。

## 使い方

1. こちらのレポジトリをクローン後、vscode にドラックアンドドロップします。

2. ワークスペースを開くか否かについて聞かれるので、開くを選択します。

3. 「このワークスペースには拡張機能の推奨事項があります。」という文面が画面に現れるので、「推奨事項を表示」を選択して必要な拡張機能をインストールしてください。

推奨事項に入れている拡張機能は以下の通りです。

- junstyle.php-cs-fixer

4. 以下のコマンドで composer.json 内のライブラリをインストールします。

```
composer install
```

5. あとは src/配下の hoge.php に整形したいコードをペーストしてファイルを保存しましょう。format.onsave により、自動整形が走ります。

## 一例

### フォーマット前

```
<?php

namespace App\Models;

use Illuminate\Database\Eloquent\Factories\HasFactory;
use Illuminate\Database\Eloquent\Model;

class Product extends Model
{
protected $fillable = [
'uuid', 'name', 'price',
];

protected $hidden = [
'id','created_at','updated_at'
];
use HasFactory;
}
```

### フォーマット後

```
<?php

namespace App\Models;

use Illuminate\Database\Eloquent\Factories\HasFactory;
use Illuminate\Database\Eloquent\Model;

class Product extends Model
{
    use HasFactory;
    protected $fillable = [
    'uuid', 'name', 'price',
    ];

    protected $hidden = [
    'id','created_at','updated_at'
    ];
}
```


## 懸念点

- 意味ごとに改行などはしないので、適宜手動で改行が必要です。
- ~~htmlが混在するファイルでは、format html in php がコードを整形しています。これによりphpのコード部分の整形がうまくいかない可能性があります。~~
- php-cs-fixerでhtmlの整形も可能にできました。(2022/11/23)