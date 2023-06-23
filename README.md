# VRCDynamicPoster

[![Deploy](https://github.com/shino-hinaduki/VRCDynamicPoster/actions/workflows/deploy.yml/badge.svg?branch=master)](https://github.com/shino-hinaduki/VRCDynamicPoster/actions/workflows/deploy.yml)

Unity を立ち上げずに内容編集できることを目指したワールド/パブリックアバター紹介ポスターです。

本リポジトリは、内容物の編集・生成を担当します。

Boothでも公開しました
https://azarashino.booth.pm/items/4141397

## 使い方

- 本リポジトリを fork します
- GitHub Action が実行されるように設定し、GitHub Pages として公開します。 公開する branch は gh-pages に設定すること
- GitHub Pages に公開した URL を、World 向けアセット ([VRCDynamicPosterPrefab](https://github.com/shino-hinaduki/VRCDynamicPosterPrefab)) に設定します

## 追加方法

`asset` ディレクトリに World/Avatar の Id をファイル名にした png 画像を入れて Commit すると自動で更新されます。

自分で編集しても良いですし、ワールド利用者から Pull Request を貰う形で運用しても良さそうです。

### Id の調べ方

World Id はブラウザからワールドの Public Link を開くと、url 上で確認できます。

例えば [https://vrchat.com/home/world/wrld_bf5bc59f-8daf-482f-bb95-cad5b465173a](https://vrchat.com/home/world/wrld_bf5bc59f-8daf-482f-bb95-cad5b465173a) の場合、 wrld_bf5bc59f-8daf-482f-bb95-cad5b465173a の部分が相当します。

Avatar Id も指定可能です。 _但し、ペデスタル公開して問題ないか確認した上でご利用ください。利用規約に反するアバターを公開する目的での利用は禁止とします。_

### GitHub を使いたくない

本リポジトリの内容をローカルで実行すれば同様の生成物を得られます。
詳しい手順は `.github/workflows/deploy.yml` を参照。dotnet core + ffmpeg 環境 もしくは Docker の実行環境と、生成物を公開する場所が必要です。

```shell
# Docker composeを利用する場合
$ docker-compose run generate_image
$ docker-compose run generate_index_video
$ docker-compose run generate_poster_video
```

## 参照技術

- ["VRChat イベントカレンダー Prefab【毎日自動更新】" by TsubokuLab Store](https://booth.pm/ja/items/1223535)
  - 動的に生成した画像を、VRChat 上で表示する
- ["【VRCAdvent Calendar】VRChat へ外部から文字列を渡すよ（C# only）" by 神城デジタル事務所](https://kamishiro.online/archives/215)
  - 動画として再生して、表示された画像を Texture2D に書き込み U#から取り扱う
